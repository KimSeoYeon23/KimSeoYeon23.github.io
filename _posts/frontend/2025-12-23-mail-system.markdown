---
layout: post
title:  "[DevLog] AI 메일 자동응답 시스템에서 이미지 처리하기 (CID vs Base64)"
date:   2025-12-23 14:33:29 +0900
categories: frontend
comments: true
published: false
---

* this unordered seed list will be replaced by the toc
{:toc}


최근 회사 메일 계정과 연동하여 **"메일 자동응답 서비스"**를 개발했습니다. 메일 서버를 크롤링해 내용을 가져오고, AI가 분석하여 적절한 답변을 생성한 뒤 답장을 발송하는 시스템입니다.

이 과정에서 가장 까다로웠던 문제는 바로 **"이미지 처리"**였습니다. 메일 프로토콜에서 사용하는 이미지 방식과, 웹 브라우저 및 API가 선호하는 방식이 서로 달랐기 때문입니다.

오늘은 이 간극을 해결하기 위해 개발한 **이미지 변환 유틸리티(CID ↔ S3, Base64 → CID)** 구현 과정을 공유합니다.


## 1. 문제 상황 (The Problem)

### 문제 A: "엑박"이 뜨는 수신 메일 (View Issue)
메일 프로토콜(MIME)에서는 본문에 삽입된 이미지를 `src="cid:image001.jpg"`와 같이 **Content-ID (CID)** 형태로 참조합니다. 하지만 웹 브라우저는 `cid:` 스키마를 해석할 수 없습니다. 때문에 크롤링한 HTML을 그대로 웹 뷰어에 띄우면 이미지가 모두 깨져서 보입니다.

### 문제 B: 전송 실패와 토큰 초과 (Send Issue)
답장을 보낼 때 웹 에디터(WYSIWYG)에 이미지를 붙여넣으면, 이 이미지는 거대한 **Base64 문자열**(`data:image/png;base64,...`)로 변환됩니다.
1.  **용량 폭발:** Base64는 원본보다 용량이 약 33% 더 큽니다.
2.  **API 제한:** 이 거대한 문자열을 그대로 백엔드나 AI 모델에 보내면 **Payload Too Large** 에러가 발생하거나, AI 토큰 한도를 순식간에 초과해버립니다.

## 2. 해결책: 이미지 변환 파이프라인 구축

이 두 가지 문제를 해결하기 위해 상황에 맞춰 이미지 경로를 스와핑(Swapping) 해주는 유틸리티 함수들을 구현했습니다.

### Solution A. 수신 시: CID → S3 URL 변환

크롤링 시점에 메일 서버에서 이미지를 추출하여 S3 같은 스토리지에 업로드하고, 그 매핑 정보(`imageInfoArray`)를 가지고 있다고 가정합니다. 브라우저 렌더링 직전에 HTML 내의 `cid:` 경로를 실제 접근 가능한 **HTTP URL**로 교체해 줍니다.

```javascript
// cid -> s3 (메일 조회용)
export const convertCidToS3 = (imageInfoArray, content) => {
  if (!imageInfoArray || !Array.isArray(imageInfoArray) || !content) {
    return content
  }

  let processedContent = content
  // 매칭 우선순위를 위해 역순 정렬 등의 전략 사용 가능
  const reversedImageInfo = [...imageInfoArray].reverse()
  
  // DOM 조작을 위해 가상 엘리먼트 생성
  const dom = document.createElement('div')
  dom.innerHTML = processedContent
  const imgList = dom.querySelectorAll('img')

  for (const imgElem of imgList) {
    const src = imgElem.getAttribute('src')

    // src가 'cid:'로 시작하는 경우 탐색
    if (src && src.includes('cid:')) {
      const cidValue = src.replace('cid:', '')
      
      // 메타데이터에서 일치하는 CID를 찾아 S3 URL로 교체
      const matchingImage = reversedImageInfo.find(imageInfo => imageInfo.cid === cidValue)

      if (matchingImage && matchingImage.imageURL) {
        processedContent = processedContent.replace(src, matchingImage.imageURL)
      }
    }
  }

  return processedContent
}
```

이제 사용자들은 깨진 아이콘 대신 정상적인 이미지가 포함된 메일 본문을 확인할 수 있습니다.

---

### Solution B. 발송 시: Base64 → CID 변환

답장 작성 시 에디터에 포함된 Base64 이미지를 감지하여 서버에 업로드하고, **CID**로 변환하여 메일 전송 API에 태웁니다. 이렇게 하면 API 요청 본문(Body)의 크기를 획기적으로 줄일 수 있습니다.

```javascript
import { fileUploadBase64 } from "@/api/penpal.js";

// base64 -> cid (메일 발송용)
export const convertBase64ToCid = async (content, editorElement = null) => {
  try {
    const imageList = []
    
    // 에디터 내의 Base64 이미지 추출
    const imgList = editorElement.querySelectorAll('img')
    for (const imgElem of imgList) {
      const imageSrc = imgElem.getAttribute('src')
      if (imageSrc && imageSrc.includes('data:image/') && imageSrc.includes('base64')) {
        imageList.push(imageSrc)
      }
    }

    if (imageList.length === 0) {
      return { content, convertImageList: '' }
    }

    // 1. 서버에 이미지 일괄 업로드 (Base64 -> File -> S3 Upload -> CID 생성)
    const response = await fileUploadBase64({ image: imageList })

    if (!response || response.length === 0) {
      return { content, convertImageList: '' }
    }

    let processedContent = content
    const convertImageList = JSON.stringify(response)
    
    // 2. 본문의 Base64 문자열을 서버에서 받은 'cid:...' 로 치환
    for (let i = 0; i < response.length; i++) {
      if (processedContent.includes(imageList[i])) {
        const cid = `cid:${response[i].cid}`
        processedContent = processedContent.replace(imageList[i], cid)
      }
    }

    return {
      content: processedContent,
      convertImageList: response // 백엔드에 전달할 매핑 정보
    }

  } catch (error) {
    console.error(`Base64 to CID conversion error: ${error.message}`)
    return { content, convertImageList: '' }
  }
}
```

이 과정을 통해 수 MB에 달하던 요청 데이터가 단 몇 KB로 줄어들었고, AI 모델 연동 시 토큰 초과 문제도 해결되었습니다.


## 3. 마치며

메일 서비스는 단순히 텍스트를 주고받는 것 같지만, 그 내부에는 `MIME`, `CID`, `Base64` 등 오래된 표준과 웹 표준 사이의 충돌이 존재합니다.

이번 작업을 통해 **"사용자에게는 익숙한 웹 경험(URL)을 제공하고, 시스템 내부적으로는 메일 표준(CID)을 준수"**하는 파이프라인을 완성할 수 있었습니다. 덕분에 이미지 깨짐이나 전송 오류 걱정 없이 안정적인 자동응답 시스템을 구축할 수 있었습니다.