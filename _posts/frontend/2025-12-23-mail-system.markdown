---
layout: post
title:  "[DevLog] 메일 서비스 개발기: CID와 Base64 사이에서 이미지 처리하기"
date:   2025-12-23 14:33:29 +0900
categories: frontend
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}


최근 사내 메일 연동 서비스를 개발하면서 **"메일 본문의 이미지 처리"** 문제로 골머리를 앓았습니다. 메일 프로토콜(SMTP/MIME)에서 이미지를 다루는 방식과, 우리가 흔히 쓰는 웹(Web) 기술이 선호하는 방식이 완전히 달랐기 때문입니다.

이 글은 그 간극을 메우기 위해 **CID(Content-ID)**와 **Base64**를 상호 변환하며 문제를 해결한 과정에 대한 기록입니다.


## 1. 직면한 문제 (The Problem)

### 문제 A: 웹에서 엑박이 뜨는 이유 (수신 시)
메일 클라이언트는 본문에 포함된 이미지를 `src="cid:image_123"` 형태로 참조합니다. 하지만 브라우저는 이 `cid:` 프로토콜을 해석할 수 없습니다. 따라서 서버에서 가져온 메일 HTML을 그대로 렌더링 하면 이미지가 모두 **'엑박(Broken Image)'**으로 표시됩니다.

### 문제 B: API 페이로드가 폭발하는 이유 (발송 시)
반대로 웹 에디터(WYSIWYG)에서 이미지를 첨부하면 `src="data:image/png;base64..."` 형태의 Base64 문자열이 됩니다.
문제는 이 문자열이 너무 길다는 것입니다. 원본 파일보다 용량이 약 33% 커지며, 이대로 백엔드 API를 호출하면 **Payload Too Large** 에러가 발생하거나 AI 모델의 토큰 제한을 초과하게 됩니다.

## 2. 해결 전략: 이미지 파이프라인 구축

이 문제를 해결하기 위해 **"상황에 맞는 이미지 경로 치환(Swapping)"** 전략을 세웠습니다.

1.  **View 모드:** `cid:` → `http URL` (브라우저가 이해할 수 있게 변환)
2.  **Edit 모드:** `Base64` → `cid:` (서버 전송 효율을 위해 변환)

## 3. 구현 코드 (Refactoring)

실제 프로젝트 코드를 기반으로, 핵심 로직만 간추려 일반화한 유틸리티 함수들입니다.

### Solution 1. 수신 메일 처리 (CID → URL)

메일 서버에서 파싱 된 이미지 정보(`attachments`)를 이용해 HTML 내의 `cid` 경로를 실제 접근 가능한 URL로 교체합니다.

```javascript
/**
 * 메일 본문의 cid 경로를 실제 이미지 URL로 치환합니다.
 * @param {Array} attachments - 메일 첨부파일(이미지) 정보 배열
 * @param {string} htmlContent - 메일 본문 HTML
 */
export const replaceCidWithUrl = (attachments, htmlContent) => {
  if (!attachments || !htmlContent) return htmlContent;

  // DOM 파싱을 위한 가상 엘리먼트 생성
  const wrapper = document.createElement('div');
  wrapper.innerHTML = htmlContent;
  
  const images = wrapper.querySelectorAll('img');

  images.forEach((img) => {
    const src = img.getAttribute('src');

    // 'cid:' 프로토콜을 사용하는 이미지 탐색
    if (src && src.startsWith('cid:')) {
      const contentId = src.replace('cid:', '');
      
      // 첨부파일 목록에서 해당 CID를 가진 이미지 매칭
      const targetImage = attachments.find(file => file.contentId === contentId);

      if (targetImage && targetImage.url) {
        img.setAttribute('src', targetImage.url);
      }
    }
  });

  return wrapper.innerHTML;
};
```

### Solution 2. 발송 메일 처리 (Base64 → CID)

사용자가 에디터에 붙여넣은 Base64 이미지를 감지하여, 서버에 먼저 업로드하고 `cid`로 변환합니다. 이를 통해 API 요청 본문을 획기적으로 줄일 수 있습니다.

```javascript
/**
 * 본문의 Base64 이미지를 서버에 업로드하고 CID로 변환합니다.
 */
export const processBase64Images = async (htmlContent) => {
  try {
    const wrapper = document.createElement('div');
    wrapper.innerHTML = htmlContent;
    
    const images = wrapper.querySelectorAll('img');
    const base64Images = [];

    // 1. Base64 이미지 추출
    images.forEach((img) => {
      const src = img.getAttribute('src');
      if (src && src.startsWith('data:image/')) {
        base64Images.push(src);
      }
    });

    if (base64Images.length === 0) return { content: htmlContent };

    // 2. 서버 업로드 (가상의 API 호출)
    // 실제로는 여기서 백엔드 API를 호출하여 이미지를 저장하고 CID를 발급받습니다.
    const uploadResult = await uploadImagesAPI(base64Images); 

    // 3. 변환된 CID로 src 교체
    let processedContent = htmlContent;
    
    uploadResult.forEach((item, index) => {
      // 원본 Base64 문자열을 'cid:...' 로 치환
      if (processedContent.includes(base64Images[index])) {
        processedContent = processedContent.replace(
          base64Images[index], 
          `cid:${item.cid}`
        );
      }
    });

    return { 
      content: processedContent, 
      uploadedImages: uploadResult 
    };

  } catch (error) {
    console.error('Image processing failed:', error);
    return { content: htmlContent }; // 에러 발생 시 원본 반환
  }
};
```

## 4. 마치며

메일 서비스는 겉보기엔 단순 텍스트 전송 같지만, 그 내부에는 **레거시 프로토콜(MIME)과 모던 웹 기술 간의 충돌**이 존재했습니다.

이번 작업을 통해 사용자는 **웹에서 깨짐 없는 이미지를 보고**, 개발팀은 **API 리소스를 효율적으로 관리**할 수 있는 파이프라인을 구축하게 되었습니다. 데이터의 형태(Format)를 상황에 맞게 유연하게 변환하는 것이 프론트엔드 개발의 중요한 역량임을 다시 한번 느꼈습니다.