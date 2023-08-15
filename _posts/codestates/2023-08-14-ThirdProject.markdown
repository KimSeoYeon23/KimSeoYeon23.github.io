---
layout: post
title:  "CodeStates BEB 마지막 프로젝트 회고"
date:   2023-08-14 10:30:00 +0900
categories: 
  - Dev
  - codestates
tag: codestates
comments: true
toc: true
toc_sticky: true
---

![CleanMile](../../assets/img/codestates/cleanmile/clean_mile_logo_2.png){:.centered}

* this unordered seed list will be replaced by the toc
{:toc}

## 프로젝트 기간 : 2023.07.17 ~ 2023.08.11
{:toc}

## 개요  
{:toc}

### 프로젝트 명  
{:toc}

**Clean Mile**  
배포 링크
- [사용자](https://www.clean-mile.co/)
- [관리자](https://admin.clean-mile.co/)

### 📝 서비스 소개
{:toc}

 환경 보호 행사에 대한 정보를 한 곳에 모아서 접근성과 사용자 편의성을 증진시키고, 행사에 참여하는 사용자들에게 인증 배지(NFT)를 발급하여 수집욕을 자극함으로써 활발한 행사 참여를 유도하는 것을 목표로 하는 환경 캠페인 플랫폼이자 온라인 커뮤니티 서비스입니다.

 이 프로젝트는 환경과 관련된 이슈에 관심이 있는 사람들 간의 상호작용을 촉진하고, 참여자들이 환경 보호를 위한 다양한 활동에 자발적으로 참여하도록 유도하여 도시 미관 훼손, 배수 시설 훼손, 생물 다양성 훼손, 대기 오염, 자원 고갈 등의 환경 문제를 해결하고 개선하는 데 기여하고자 하는 아이디어에서 시작하였습니다.

### 🚗 주요 기능
{:toc}

- **이벤트 관리**: 다양한 환경과 관련된 행사를 하나의 플랫폼에서 관리하여 사용자들에게 접근성과 편의성을 제공합니다.
- **커뮤니티**: 서비스 사용자들에게 정보 교환 및 소통의 장을 제공합니다.
- **DNFT(ERC-721)** : 회원가입 시 최초로 사용자들에게 DNFT를 지급합니다. 사용자들은 활동을 통해 DNFT 업그레이드가 가능합니다.
- **Badge(ERC-1155)** : 사용자들은 행사 참여 후 인증 시 행사와 관련된 배지를 얻을 수 있습니다.
- **행사** **참여 인증** : 행사의 참가자들은 행사가 끝난 뒤 QR 코드를 통해서 참여 인증을 할 수 있습니다.
- **마일리지, 토큰(ERC-20)** : 사용자들은 리뷰 작성을 통해 마일리지를 획득할 수 있고, 마일리지를 토큰을 교환 가능합니다.
- **관리자** : 관리자는 별도의 관리자 페이지를 통해 행사, 유저, 댓글을 관리합니다.

### 🎯서비스 대상
{:toc}

 Clean Mile 프로젝트는 [플로깅](https://namu.wiki/w/%ED%94%8C%EB%A1%9C%EA%B9%85) 및 [비치코밍](https://gscaltexmediahub.com/esg/gsc-esg/beachcoming/)과 같은 환경 보호와 운동을 동반하는 활동들을 중점적으로 다루고 있습니다. 이러한 활동들은 최근 SNS을 통해 국내에 전파되고 있으며 강변 지역에서 청년들을 중심으로 활발한 활동이 이루어지고 있습니다. 국내외 기업들은 이러한 MZ세대를 겨냥해 플로깅과 비치코밍 등의 행사를 주최하고 SNS에 업로드할 수 있는 인증샷을 찍을 수 있는 장소를 마련하거나 행사에 참여한 것을 기념하기 위한 기념품을 지급하고 있습니다. 이러한 트렌드에 합류하기 위해 저희는 주요 서비스 대상을 국내에 거주하는 청년 및 청소년층으로 지정하였습니다.

 한편 저희 플랫폼은 NFT, FT같은 블록체인에 기반한 인센티브를 지급하고 있으므로 서비스의 사용자는 블록체인 기반 기술에 대한 기본적인 이해가 필요합니다. 따라서 주된 사용자 계층은 블록체인과 관련된 개념을 빠르게 습득할 수 있거나 이미 블록체인에 익숙한 청년 및 청소년 계층이 될 것입니다. 그렇다고 NFT나 블록체인에 대한 개념을 알아야만 저희 플랫폼의 서비스를 이용하고 흥미를 느낄 수 있는 것은 아닙니다. 추후에 서비스가 더욱 발전해감에 따라 환경과 건강에 관심이 있는 모든 사람들이 저희의 서비스의 사용자가 될 가능성을 염두에 두고 있습니다.

### 🍀플랫폼 지속 가능성
{:toc}

 프로젝트의 주제가 ‘환경’과 관련된 만큼 선한 의도와 선한 영향력을 가진 사람들에게 저희 프로젝트의 가치를 이해시킬 수 있어야 합니다. 그런데 봉사하는 마음으로 선뜻 손을 내밀어 준 이에게 수수료를 부담하게 한다면 이것은 과연 옳은 일일까요? 이에 저희는 서비스 주체로서 서비스 내에서 발생하는 모든 트랜잭션 비용을 저희가 부담을 하고 사용자들에게는 비용을 청구하지 않는 방향으로 나아가기로 했습니다.

 그런데 한 편으로 모든 트랜잭션 비용을 부담한다는 것이 상당한 부담이 될 것이라 판단했습니다. 이에 저희는 온체인 데이터 최소화, 트랜잭션 회수 최소화 등 여러 부분에서 비용을 최소화하기 위해 고민했습니다. 나아가 운영에 필요한 비용들은 행사 주최자들 또는 사용자들의 후원, 추후에 플랫폼에 많은 사용자들이 유입된다면 그로부터 발생하는 여러 광고 비용으로 충당하기로 결정했습니다.

### 🌐Blockchain Network
{:toc}

저희 팀은 저희 프로젝트에 어떤 블록체인 네트워크가 가장 잘 맞을지 고민했습니다. 그 중에서도 이더리움 사용량이 많아지면서 이더리움 메인넷의 성능을 올리고 높은 수수료 문제를 해결하기 위해 이더리움 블록체인에 레이어 2 스케일링 솔루션을 도입하여 사용자들이 보다 저렴한 수수료로 편리하게 서비스를 이용할 수 있도록 한 폴리곤 네트워크가 가장 적당하고 생각했습니다. 그리고 **폴리곤 네트워크**가 가진 주된 가치도 web3 기술의 발전과 함께 환경에 대한 문제도 항상 고민하는 방향이기 때문에 저희 프로젝트와 잘 맞다고 생각했습니다.

****

## 포지션
{:toc}

마지막 프로젝트는 내가 원하던 드림팀이 되었다고 생각한다. 그렇지만 나를 제외하고 다른 팀원 분들은 모두 백엔드나 컨트랙트 포지션이라 프론트엔드는 나 혼자인건 마찬가지였다. 이번 프로젝트는 두 번째 프로젝트의 연장선 이지만 기획을 바꿔 Back Office가 추가되어 할 일이 배로 늘어났다. 그래서 내가 Front Office의 프론트엔드를 맡게 되고 팀장님이 Back Office의 프론트엔드 포지션을 맡게 되었다.

***

## 팀 규칙 
{:toc} 

### 그라운드 룰 
{:toc} 

1. 10시 스탠드 업 미팅 (전날 작성한 코드 설명, 오늘 목표)
2. 5시 진행도 공유 (카메라 ON)
3. 바른 말 고운 말 사용하기
4. 개인사정이 생길 경우, 팀원들에게 미리(오전 중으로) 알리기
5. 질문이 있는 경우, 디스코드 또는 줌에서 바로 호출
6. 오류 발생 시, 일단 해결하려고 노력해보고 30분 이상 붙들고 있지 말 것. 그리고 오류 제보 채널에 오류 로그를 복사 붙여넣기 또는 화면 캡쳐하여 올리고 줌으로 호출

### 깃허브 브랜치 관리 규칙  
{:toc}

1. main, dev 브랜치는 팀장이 직접 관리 (팀장 허가 필요)
2. pull request를 작성하면 디스코드 또는 줌으로 팀장 호출
3. 브랜치 merge가 완료되면 팀장은 팀원들에게 공지
4. 브랜치 자동 생성 설명
    1. 브랜치를 생성하기 위해서 먼저 리포지토리 상단에 있는 `Issues` 탭을 선택
    2. New Issue → Issue Task Card (Get Started) 선택
    3. Task 카드를 작성하고 오른쪽에 있는 labels 칸에서 enhancement를 선택 (나머지도 적당히 채워줍시다)
    4. Submit new issue → `feat/[이슈 번호]`이름으로 새로운 브랜치 자동 생성

### 커밋 메시지 규칙
{:toc}

```
Fix: 올바르지 않은 동작을 고친 경우
Add: 파일 또는 새로운 기능 추가가 있을 때
Remove: 코드나 파일의 삭제가 있을 때
Update: 기존의 코드를 수정, 추가, 보완
Refactor: 전면 수정
Rename: 이름 변경 (디렉토리, 파일, 함수, 변수 등)
```

> git commit -m "Add 영어로 제목 적기"

### 커밋 순서
{:toc}

```
1. git add .
2. git commit "커밋 메시지"
3. git fetch origin dev
4. git rebase origin/dev
5. git push origin 작업중인 브랜치
6. 브랜치에서 작업을 마친 경우, pull request 생성
```

### .gitignore 기본 설정
{:toc}

```
node_modules
.env
config.json
package-lock.json
.DS_Store
```

> .env를 ignore하는 대신 .env.example로 어떤 값이 필요한지 명시

### node, npm 버전 정보
{:toc}

```
1. node - 16.14.0
2. npm - 9.6.4
```

### Linter
{:toc}

```
- VSCode Prettier extension 사용
- 1 tab = 공백 4칸
```

***

## 구현 목표  
{:toc}

### 사용자
{:toc}

**Bare Minimum**  

- 회원 가입 (이메일 인증 또는 SNS 연동) → 지갑 연동? 클레이튼 서비스체인?
- 로그인, 로그아웃
- 행사 정보 리스트 확인
- 행사 정보 상세 페이지 확인
- 행사 참여 신청
- 참여 인증 (인증 방식: qr 코드 찍기) 및 배지(NFT) 수령
- 참여 인증 뒤에 후기 작성 (토큰 보상 지급)
- 로그인한 사용자 마이 페이지 확인 (DNFT 업그레이드 포함)
- 개인 정보 수정
- 커뮤니티 게시판에서 게시물 리스트 확인
- 커뮤니티 게시물 작성, 수정, 삭제
- 게시물에 댓글 작성, 수정, 삭제
- 다른 사용자 마이 페이지 확인  
  
**Advanced**  

- 회원 탈퇴
- 토큰 전송
- 우수 회원(골드 이상)들이 소규모 행사를 주최 가능 (보상 NFT x)
- 비밀번호 찾기
- 게시물 수정 시, 이미지 추가 또는 삭제
- 회원가입, 로그인 페이지에 three.js 애니메이션 추가
- 유저 인스타그램 연동

**Nightmare**

- 게시물 작성 시 SNS(인스타그램) 연동으로 동시 게시
- 토큰으로 배지 교환 (소규모 행사 참여자들은 배지를 보상으로 받는 대신 구매)  

### 관리자
{:toc}

**Bare Minimum**  

- 관리자 로그인
- 사용자 관리
- 커뮤니티 게시판 관리
- 댓글 관리
- 행사 등록
- 행사에 참여 신청한 사용자 리스트 확인
- 행사 참여 확정된 사용자 목록 확인 및 엑셀 파일로 다운로드
- 행사 참여 인증을 받은 사용자 목록 확인
- 행사 참여 인증 및 후기 작성자 목록 확인
- NFT 민팅
- 참여 인증된 사용자에게 NFT 발급
  
**Advanced**  

- 토큰으로 교환 가능한 배지 등록
- 탈퇴한 유저 관리
- 행사 참가 확정 메시지 전송
- 기업형 사용자 계정 발급
- 관리자가 기업형 사용자에게 NFT 발급 권한 부여

프론트엔드의 목표는 이렇다. Bare Minimum을 최소 목표로 잡고, 해당 기능들을 모두 구현하고 시간이 남을 경우 Advanced, Nightmare를 구현하기로 정했다.

---

## 프로젝트 기획
{:toc}

![서비스아키텍쳐](../../assets/img/codestates/cleanmile/service_archtecture.png){:.centered}
*서비스 아키텍쳐*  

![회원가입/로그인 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_signup_signin.png){: width="350" height="350"} | ![사용자 개인페이지 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_mypage.png){: width="350" height="350"} | ![행사 참여 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_events.png){: width="350" height="50"} | ![게시판 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_posts.png){: width="350" height="350"}

*사용자 플로우 차트*

![행사 등록 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_admin_event_create.png){: width="350" height="350"} | ![행사 진행 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_admin_event_entries.png){: width="350" height="350"} | ![사용자 관리 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_admin_user.png){: width="350" height="50"} | ![게시글 관리 플로우차트](../../assets/img/codestates/cleanmile/flow_chart_admin_posts.png){: width="350" height="350"}

*관리자 플로우 차트*  

![사용자 와이어 프레임](../../assets/img/codestates/cleanmile/wireframe_user.png){:.centered}
*사용자 와이어 프레임*  

![관리자 와이어 프레임](../../assets/img/codestates/cleanmile/wireframe_admin.png){:.centered}
*관리자 와이어 프레임*  

보시다시피 처음의 기획 단계 에서는 기업형 관리자 계정이 따로 있었다. 그러나 멘토 분과 면담 중 현재 굳이 기업형 관리자가 따로 필요하지 않다고 정했고, 프로젝트의 볼륨을 조금 줄이기 위해 기업형 관리자는 우선 없애기로 정했다. 따라서 이벤트나 유저에 관한 것은 모두 관리자가 관리하고, 기업형 관리자는 Advanced로 분류하기로 했다.

## 기술 스택
{:toc}

**Front-end**  
<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26.svg?style=for-the-badge&logo=HTML5&logoColor=white"/>
<img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=CSS3&logoColor=white"/>
<img alt="Typescript" src="https://img.shields.io/badge/Typescript-3178C6.svg?style=for-the-badge&logo=Typescript&logoColor=white"/>
<img alt="Javascript" src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=for-the-badge&logo=JavaScript&logoColor=white"/>
<img alt="Next.js" src="https://img.shields.io/badge/Next.js-000000.svg?style=for-the-badge&logo=Next.js&logoColor=white"/>
<img alt="Tawilwind CSS" src="https://img.shields.io/badge/Tailwind CSS-06B6D4.svg?style=for-the-badge&logo=TailwindCSS&logoColor=white"/>
<img alt="Redux" src="https://img.shields.io/badge/Redux-764ABC.svg?style=for-the-badge&logo=Redux&logoColor=white"/>
<img alt="Redux Saga" src="https://img.shields.io/badge/reduxsaga-999999.svg?style=for-the-badge&logo=reduxsaga&logoColor=white"/>
<img alt="React Query" src="https://img.shields.io/badge/reactquery-FF4154.svg?style=for-the-badge&logo=reactquery&logoColor=white"/>
<img alt="Next Translate" src="https://img.shields.io/badge/next translate-26A69A.svg?style=for-the-badge&logo=i18next&logoColor=white"/>
<img alt="Axios" src="https://img.shields.io/badge/Axios-5A29E4.svg?style=for-the-badge&logo=Axios&logoColor=white"/>
<img alt="web3.js" src="https://img.shields.io/badge/web3.js-F16822.svg?style=for-the-badge&logo=web3.js&logoColor=white"/>
<img alt="three.js" src="https://img.shields.io/badge/three.js-000000.svg?style=for-the-badge&logo=three.js&logoColor=white"/>
<img alt="SweetAlert2" src="https://img.shields.io/badge/SweetAlert2-FF6666.svg?style=for-the-badge&logo=SweetAlert2&logoColor=white"/>

**Back-End**  
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
<img src="https://img.shields.io/badge/node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white">
<img src="https://img.shields.io/badge/express-000000?style=for-the-badge&logo=express&logoColor=white">
<img src="https://img.shields.io/badge/jsonwebtokens-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white">
<img src="https://img.shields.io/badge/mongodb-47A248?style=for-the-badge&logo=mongodb&logoColor=white">
<img src="https://img.shields.io/badge/mocha-8D6748?style=for-the-badge&logo=mocha&logoColor=white">
<img src="https://img.shields.io/badge/chai-A30701?style=for-the-badge&logo=chai&logoColor=white">
<img src="https://img.shields.io/badge/jest-C21325?style=for-the-badge&logo=jest&logoColor=white">
<img src="https://img.shields.io/badge/postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white">
<img src="https://img.shields.io/badge/ethers.js-3C3C3D?style=for-the-badge&logoColor=white">
<img src="https://img.shields.io/badge/aws_sdk-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white">
<img src="https://img.shields.io/badge/amazons3-569A31?style=for-the-badge&logo=amazons3&logoColor=white">

**Blockchain**  
<img src="https://img.shields.io/badge/solidity-363636?style=for-the-badge&logo=solidity&logoColor=white">
<img src="https://img.shields.io/badge/openzeppelin-4E5EE4?style=for-the-badge&logo=openzeppelin&logoColor=white">
<img src="https://img.shields.io/badge/mocha-8D6748?style=for-the-badge&logo=mocha&logoColor=white">
<img src="https://img.shields.io/badge/chai-A30701?style=for-the-badge&logo=chai&logoColor=white">
<img src="https://img.shields.io/badge/hardhat-000000?style=for-the-badge&logo=hardhat&logoColor=white">

**Daemon**  
<img src="https://img.shields.io/badge/pm2-2B037A?style=for-the-badge&logo=pm2&logoColor=white">

**Infra**  
<img src="https://img.shields.io/badge/githubactions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white">
<img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white">
<img src="https://img.shields.io/badge/amazon_aws-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white">

### Next.js
{:toc}

Next.js는 리액트를 위해 만든 **오픈소스 자바스크립트 웹 프레임워크**로, 리액트에는 없는 **서버 사이드 렌더링(Server Side Rendering, SSR), 검색 엔진 최적화(Search Engine Optimization)**이 가능하다.

- **클라이언트 사이드 렌더링(Client Side Rendering, CSR)**
  - 리액트에서 쓰이는 **클라이언트 사이드 렌더링(Client Side Rendering, CSR)**의 경우 모든 자바스크립트 파일을 로드하고 사용자는 웹을 보게 되는데 이때까지 사용자는 많은 시간을 대기해야 한다. 또, 자바스크립트가 로드 되지 않은 경우 아무런 정보를 보이지 않는다. 구글의 검색 엔진의 경우 자바스크립트가 로드 되지 않은 페이지를 검색 엔진으로 스캔함으로 결론적으로 검색에 아무 페이지도 걸리지 않게 된다.
- **서버 사이드 렌더링(Server Side Rendering, SSR)**
  - **서버 사이드 렌더링(Server Side Rendering, SSR)**은 서버에서 자바스크립트를 로딩함으로써 클라이언트 측에서는 자바스크립트를 로딩하는 시간이 줄어들게 된다. 그리고 검색 엔진이 자바스크립트를 읽는 것이 아닌 서버측에서 자바스크립트, html, css를 만들어 컨텐츠에 직접 업로드 함으로 검색 엔진에 게시글이 걸리게 된다. 또한 meta 태그를 자유롭게 추가함으로 SEO를 용이하게 할 수 있다.

### Redux
{:toc}

- 애플리케이션의 state를 관리하기 위한 오픈소스 JavaScript 라이브러리이다.
- Redux는 원리가 간단하고 모든 수정 사항을 기록한다.
- 모든 히스토리가 기록되어 에러 추적이 쉽고 안정적이다.
- 앱이 커지면 코드를 쪼개야 하는데 Reducer들을 쪼갤 수 있어 편리하다. (Reducer는 전달 받은 action에 따라 상태를 어떻게 업데이트 할지 정의한 함수)
- Redux를 사용하면 애플리케이션 전체에 걸쳐 상태를 공유할 수 있다. 이는 React의 prop drilling 문제를 해결하는 데 도움이 된다.
  
### Redux Saga  
{:toc}

리액트/리덕스 애플리케이션에서 비동기적으로 API를 호출하여 데이터를 가져오는 일과 같은 부수 효과(Side Effect)를 쉽게 처리하기 위해 사용하는 라이브러리이다.

- 애플리케이션에서 전적으로 부수 효과(Side Effect)만을 담당하여 처리한다.
- 비동기 함수 호출 결과 데이터를 통해 성공, 실패 여부를 판단하고 상태를 업데이트시키는 등의 작업(Task)을 제어할 수 있다.
- 스토어에 접근하거나 특정 액션(Action)을 디스패치(Dispatch) 하여 다른 사가함수를 실행시킬 수 있다.
  
> 참고: <https://tech.trenbe.com/2022/05/25/Redux-Saga.html>

### Tailwind CSS
{:toc}

Tailwind CSS는 HTML 파일, JavaScript 컴포넌트와 클래스네임을 위한 다른 템플릿 모두를 스캐닝해서 대응하는 스타일을 생성하고 그것들을 정적인 CSS 파일에 입력하여 동작한다.

제로 런타임으로 동작하며 빠르고, 유연하며 믿을 수 있다.

- CSS를 작성할 때 시간을 많이 절약할 수 있다.
- 컴포넌트 생성과 관리가 쉬우며, 유지 보수하기 편하다.
- 프로그래밍 언어와 같은 추상화 수준을 제공해 스타일을 빠르게 적용할 수 있어 코드의 길이가 줄고, 개발 시간이 절약된다.
- 커스터마이징이 쉬워 원하는 대로 디자인을 변경할 수 있다.
- 반응형 디자인 구현도 쉽다.
- 클래스에 유틸리티한 이름(flex, pt-4, ...)을 붙여 HTML 내에서 개발하는 방식이다.

### React Query  
{:toc}

React-Query는 React앱에서 비동기 로직을 쉽게 다루게 해주는 라이브러리이다.

- React Query는 React Application에서 서버 상태를 불러오고, 캐싱하며, 지속적으로 동기화하고 업데이트하는 작업을 도와주는 라이브러리이다.
- 복잡하고 장호아한 코드가 필요한 다른 데이터 불러오기 방식과 달리 React Component 내부에서 간단하고 직관적으로 API를 사용할 수 있다.
- get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행한다. (예를 들면 게시판의 글을 가져왔을 때 게시판의 글을 생성하면 게시판 글을 get하는 api를 자동으로 실행 )
- 데이터가 오래 되었다고 판단되면 다시 get (invalidateQueries)
- 동일 데이터 여러번 요청하면 한번만 요청한다. (옵션에 따라 중복 호출 허용 시간 조절 가능)
- 무한 스크롤 (Infinite Queries (opens new window))
- 비동기 과정을 선언적으로 관리할 수 있다.
- react hook과 사용하는 구조가 비슷하다.

> 참고  
> <https://maintainhoon.vercel.app/blog/post/react_query>  
> <https://velog.io/@dormahd114/React-Query%EB%9E%80>

### Next Translate 
{:toc} 

Next.js 프레임워크를 사용하여 만들어진 웹 애플리케이션 다국어(i18n) 지원을 추가하기 위한 도구이다.

- 필요한 번역만을 로드하여 번역의 페이로드를 최소화한다.
- `useTranslation` 훅과 `withTranslation` 고차 컴포넌트를 제공하여 간편하게 번역을 사용할 수 있다.
- 간단한 JSON 파일을 사용하여 언어 및 번역을 구성할 수 있다.

> 참고: <https://dev-yakuza.posstree.com/ko/react/nextjs/localization/>

### SweetAlert2
{:toc}

SweetAlert2 라이브러리는 기존의 alert 창보다 다양한 디자인과 색감으로 디자인이 된 alert 창이다. 한 종류만 있는게 아니라 **alert, confirm, prompt** 입력창 역시 지원하며, 여러 주제에 따라 다양한 예쁜 알림창을 따로 CSS 작업 없이 고퀄리티의 애니메이션 창을 구성할 수 있다.

> 참고: <https://inpa.tistory.com/entry/SweetAlert2-%F0%9F%93%9A-%EC%84%A4%EC%B9%98-%EC%82%AC%EC%9A%A9>

## 구현
{:toc}

### 메인 페이지
{:toc}

![MainPage](../../assets/img/codestates/cleanmile/Info.png){:.centered}
*메인 페이지 화면*

메인 페이지는 서비스의 설명과 인스타그램 피드 게시글이 보이도록 구현했다. `Get Started` 버튼을 클릭하면 로그인 페이지로 이동하며, 로그인한 사용자인 경우 이벤트 리스트 페이지로 이동하도록 했다.  
인스타그램 게시글의 경우 원래는 인스타그램 API를 사용하여 특정 해시태그가 설정되어 있는 게시글만 가져오도록 구현하려고 했으나 시간이 부족하고 인스타그램 API 설정 중에서 `https`만 등록이 가능하여 구현을 하지 못했다. 왜인지 내 컴퓨터에서는 `mkcert`를 사용해도 local에서 인증서가 유효하지 않다고 뜨며 `https`가 적용이 안되는 상황이다. 구글에 검색해서 온갖 방법을 다 해봤는데도 되지 않았는데, 혹시 윈도우 11 이라 그런건지 왜 이런지 알 수가 없다..ㅠ 혹시 같은 상황에서 해결하신 분이 있으면 알려주시면 정말 감사할 것 같습니다,,ㅠㅠ

```tsx

/**
 * 사용자 로그인 상태를 상태로 관리
 * @type {boolean}
 */
const [isLoggedIn, setIsLoggedIn] = useState(false);

/**
 * 컴포넌트 마운트 시, 세션 스토리지에서 사용자 로그인 정보를 가져와 상태를 설정
 */
useEffect(() => {
    setIsLoggedIn(Boolean(sessionStorage.getItem('user')));
}, []);
 */

return (
 <div className='flex justify-end items-end w-full md:justify-center sm:justify-center xs:justify-center'>
  <button className='bg-main-blue hover:bg-blue-600 rounded-xl text-white font-semibold px-20 py-3 md:px-16 sm:px-12 xs:px-6 md:text-sm sm:text-sm xs:text-xs transition duration-300'
   onClick={() => isLoggedIn ? router.push('/posts/events') : router.push('/login')}>
   {t('common:Get Started')}
  </button>
 </div>
)
```

*Get Started 버튼 로그인 확인 코드*

### 회원 가입
{:toc}

![SignUp](../../assets/img/codestates/cleanmile/signup.gif){:.centered}  
*회원가입 화면*  

회원 가입 시 서버로 중복된 이메일이 있는지 체크를 하고, 중복된 이메일이 없을 경우 입력한 이메일로 이메일 인증 코드가 발송된다.
닉네임 또한 DB에서 중복된 닉네임이 있는지 중복 체크를 해야 한다.  
비밀번호는 영어 대소문자, 숫자, 특수 기호가 포함되어야 하며 최소 8자 이상으로 조건을 정했고, 모든 `Input`을 입력하고 난 후에 메타마스크 연결까지 진행해야 회원가입 버튼이 활성화 된다.  
이번에는 비밀번호의 경우 입력한 비밀번호가 어떤 문자인지 확인할 수 있는 버튼을 추가했다.  
회원가입에 성공한 이후 바로 로그인 페이지로 이동하도록 구현했다.

```tsx
  const [isPwdVisible, setPwVisible] = useState(false);
  const [isPwConfirmVisible, setPwConfirmVisible] = useState(false);
  const [formState, setFormState] = useState({
    name: '',
    phoneNumber: '',
    nickname: '',
    email: '',
    password: '',
    pwConfirm: '',
    errorMessage: '',
    emailError: '',
    pwConfirmMessage: '',
    passwordError: '',
    pwConfirmError: '',
    emailCheck: false,
    nicknameCheck: false
  });

  /**
   * 비밀번호 가시성 상태를 전환하는 함수
   */
  const passwordVisibility = () => {
    setPwVisible(!isPwdVisible);
  };
  
  /**
   * 비밀번호 확인 가시성 상태를 전환하는 함수      
   */
  const pwConfirmVisibility = () => {
    setPwConfirmVisible(!isPwConfirmVisible);
  };

  /**
   * 폼 상태를 업데이트하는 함수
   * @param {keyof typeof formState} key - 변경할 상태의 키
   * @param {any} value - 새로운 값
   */
  const updateFormState = (key: keyof typeof formState, value: any) => {
    setFormState(prev => ({ ...prev, [key]: value }));
  };

  /**
   * 주어진 유형에 따라 필드를 검증하는 함수
   * @param {"email" | "nickname" | "password" | "passwordConfirm"} type - 검증할 필드 유형
   */
  const validateField = (type: "email" | "nickname" | "password" | "passwordConfirm" | "phoneNumber") => {
    switch (type) {
      case "email":
        const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        if (!re.test(formState.email)) {
          updateFormState('emailError', '이메일 형식에 맞지 않습니다.');
          updateFormState('emailCheck', false);
        } else {
          updateFormState('emailError', '');
          updateFormState('emailCheck', true);
        }
        break;

      case "nickname":
        if (formState.nickname.length < 2) {
          updateFormState('errorMessage', t('common:Nickname must be at least 2 characters long'));
          updateFormState('nicknameCheck', false);
        } else if (formState.nickname.length > 8) {
          updateFormState('errorMessage', t('common:Nickname can be up to 8 characters'));
          updateFormState('nicknameCheck', false);
        } else {
          updateFormState('errorMessage', '');
          updateFormState('nicknameCheck', true);
        }
        break;

      case "password":
        const passwordRegex = /^(?=.*[!@#$%^&*])(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$/;
        if (formState.password.length < 8) {
          updateFormState('passwordError', t('common:Password must be at least 8 characters long'));
        } else if (!passwordRegex.test(formState.password)) {
          updateFormState('passwordError', t('common:Password must contain all English uppercase letters, lowercase letters, numbers, and special symbols'));
        } else {
          updateFormState('passwordError', '');
        }
        break;

      case "passwordConfirm":
        if (formState.password.length <= 0 && formState.pwConfirm.length <= 0) {
          updateFormState('pwConfirmError', '');
          updateFormState('pwConfirmMessage', '');
        } else if (formState.password === formState.pwConfirm) {
          updateFormState('pwConfirmMessage', t('common:Password matches'));
          updateFormState('pwConfirmError', '');
        } else if (formState.password !== formState.pwConfirm) {
          updateFormState('pwConfirmError', t("common:Password doesn't match"));
          updateFormState('pwConfirmMessage', '');
        }
      case "phoneNumber":
        let formattedNumber = formState.phoneNumber.replace(/\D/g, '');
        if (formattedNumber.length >= 4) {
            const part1 = formattedNumber.substring(0, 3);
            const part2 = formattedNumber.substring(3, 7);
            const part3 = formattedNumber.substring(7);
            formattedNumber = `${part1}-${part2}-${part3}`;
        }
        updateFormState('phoneNumber', formattedNumber);
        break;
    }
  };

  useEffect(() => {
    validateField("email");
  }, [formState.email]);

  useEffect(() => {
    validateField("nickname");
  }, [formState.nickname]);

  useEffect(() => {
    validateField("password");
  }, [formState.password]);

  useEffect(() => {
    validateField("passwordConfirm");
  }, [formState.pwConfirm]);

  useEffect(() => {
    validateField("phoneNumber");
  }, [formState.phoneNumber]);
```

*정규식 체크와 폼 상태 업데이트, 비밀번호 토글 버튼 코드*  

```tsx
/**
   * 사용자가 입력한 이메일을 검증하고 인증 코드를 발송하는 함수
   *
   * @async
   * @function checkEmail
   * @returns {Promise<void>} 아무것도 반환하지 않음
   */
  const checkEmail = async () => {
    const { email } = formState;

    try {
      const res = await userCheckEmail(email);
      if (res.status === 200) {

        Swal.fire({
          title: t('common:Success'),
          text: t('common:Your email verification code has been sent'),
          icon: 'success' as const,
          confirmButtonText: t('common:OK'),
          confirmButtonColor: '#6BCB77'
        }).then(() => {
          Swal.fire({
            title: t('common:Enter your verification code'),
            input: 'text',
            inputPlaceholder: t('common:Enter your code here'),
            confirmButtonText: t('common:Verify'),
            showCancelButton: true
          }).then((result) => {
            if (result.isConfirmed) {
              verifyEmailCode(result.value).then(() => {
                Swal.fire({
                  title: t('common:Success'),
                  text: t('common:Your email has been successfully authenticated'),
                  icon: 'success',
                  confirmButtonText: t('common:OK'),
                  confirmButtonColor: '#6BCB77'
                });
              }).catch((error) => {
                Swal.fire({
                  title: t('common:Error'),
                  text: error?.response?.data.message,
                  icon: 'error',
                  confirmButtonText: t('common:OK'),
                  confirmButtonColor: '#6BCB77'
                });
                Swal.close();
              });
            }
          });
        })
      } else if (res.status === 400) {

        dispatch(showErrorAlert(res.data.message));
      }
    } catch (error) {
      const err = error as AxiosError;
      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }

  /**
   * 사용자가 입력한 이메일 인증 코드를 검증하는 함수
   * 
   * @async
   * @function verifyEmailCode
   * @param {string} verifyCode 사용자가 입력한 이메일 인증 코드
   * @returns {Promise<void>} 아무것도 반환하지 않음
   */

  const verifyEmailCode = async (verifyCode: string) => {
    const { email } = formState;

    try {
      const res = await userVerifyEmailCode(email, verifyCode);

      if (res.status === 200) {

        dispatch(showSuccessAlert(t('common:Your email has been successfully authenticated')));
      } else {
        dispatch(showErrorAlert(res.data.message));
      }

    } catch (error) {
      const err = error as AxiosError;
      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }
```

*이메일 중복 체크 및 인증코드 발송 코드*

```tsx
/**
   * 유저가 입력하 닉네임을 중복 체크하는 함수
   * 
   * @async
   * @function checkNickname
   * @returns {Promise<void>} 아무것도 반환하지 않음
   */
  const checkNickname = async () => {
    const { nickname } = formState;

    try {
      const res = await userCheckNickname(nickname);

      if (res.status === 200) {
        dispatch(showSuccessAlert(res.data.message));
        setFormState(prevState => ({ ...prevState, nicknameCheck: false }));
      } else {
        dispatch(showErrorAlert(res.data.message));
      }
    } catch (error) {
      const err = error as AxiosError;
      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }
```

*닉네임 중복 체크 코드*

```tsx
  /**
   * 유저의 Ethereum 계정 주소를 가져오는 함수
   * 
   * @returns {Promise<string>} 첫 번째 Ethereum 계정 주소를 반환
   */
  const getUserAccount = async () => {
    let accounts = await web3.eth.getAccounts();;
    return accounts[0];
  }

  /**
   * 유저의 계정 정보를 가져오는 뮤테이션을 실행하는 함수
   * 'getUserAccount' 뮤테이션을 실행하고, 성공 시 'userAddress' 쿼리 데이터를 업데이트
   * 
   * @function fetchAccountInfo
   * @callback useMutation
   * @returns {void} 아무것도 반환하지 않음
   */
  const fetchAccountInfo = useMutation(getUserAccount, {
    onSuccess: (data) => {
      queryClient.setQueryData('userAddress', data);
    },
    onError: (error) => {
      console.log('Error: ', error);
    }
  })

  /**
   * 유저의 메타마스크 지갑을 로그인하는 함수
   * 
   * @async
   * @function loginWallet
   * @returns {Promise<void>} 아무것도 반환하지 않음
   */
  const loginWallet = async () => {

    // 유저 브라우저 확인
    let agent = navigator.userAgent.toLowerCase();

    try {
      await window.ethereum.request({ method: 'eth_requestAccounts' });
    } catch (error) {
      if (!window.ethereum) {
        // 메타마스크 설치가 안되어 있을 경우 설치 페이지로 이동
        if (agent.indexOf('chrome') != -1 || agent.indexOf('msie') != -1) {         // 크롬일 경우
          window.open(`${process.env.NEXT_PUBLIC_INSTALL_META_CHROME}`, '_blank');
        } else if (agent.indexOf('firefox') != -1) {                                // firefox일 경우
          window.open(`${process.env.NEXT_PUBLIC_INSTALL_META_FIREFOX}`, '_blank');
        }
      }
    }

    fetchAccountInfo.mutate();
  };
```

*메타마스크 연결 코드*

```tsx
  /**
   * 유저의 회원가입 정보를 서버에 전송하는 함수
   * 
   * 요청이 성공적으로 처리되면, alert를 통해 성공 메시지를 보여주고 로그인 페이지로 이동
   * 요청이 실패하면, alert를 통해 오류 메시지를 보여줌
   * 
   * @async
   * @function signUp
   * @returns {Promise<void>} 아무것도 반환하지 않음
   */
  const signUp = async () => {
    Swal.fire({
      title: t('common:Loading'),
      allowOutsideClick: false,
      didOpen: () => {
        Swal.showLoading();
      }
    });

    const { email, name, phoneNumber, password, nickname } = formState;

    let walletAddress;
    if (userAddressQuery.data) {
      walletAddress = String(userAddressQuery.data);
    }

    try {
      const res = await userSignUp(email, name, phoneNumber, password, nickname, walletAddress, 'none');

      Swal.close();

      if (res.status === 200) {
        dispatch(showSuccessAlert(res.data.message));
        router.push('/login');
      }

    } catch (error) {
      Swal.close();

      const err = error as AxiosError;
      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }
```

*회원가입 코드*

### 로그인
{:toc}

![SignUp](../../assets/img/codestates/cleanmile/login.gif)
*로그인 화면*  

로그인이 완료되면 메인 페이지로 자동으로 이동이 된다. 로그인을 하지 않아도 모든 게시글 조회는 가능하다. 하지만 게시글 작성이나 댓글 작성, 이벤트 참여의 경우 로그인을 해야만 가능하다. 로그인을 하지 않은 상태로 진행하려 할 경우 로그인 페이지로 이동하도록 구현했으며, 이에 대한 코드는 각 컴포넌트에 구현되어 있어 깃허브에서 확인이 가능하다.  
로그인이 성공적으로 되면 `React Query`를 사용하여 유저 정보를 캐싱하여 `sessionStorage`에 저장할 수 있도록 구현했다. 유저의 로그인 체크와 로그인 했을 경우의 헤더 상태를 변경하기 위해 이러한 방법으로 구현을 진행했는데, 아직까지 나는 이러한 방법 말고 다른 방법으로는 있는지 모르겠고 시도해보지 못했다. 더 나은 방법이 있는지 계속해서 찾아봐야 할 것 같다.

```tsx
  const queryClient = useQueryClient();

  /**
   * 로그인 성공 시 호출되는 함수
   * @param {LoginAPIOutput} data - 로그인 API의 응답 데이터
   * @param {LoginAPIInput} variables - 로그인 API의 입력 데이터
   * @param {unknown} context - 알 수 없는 컨텍스트 데이터
   */
  const handleLoginSuccess = (data: LoginAPIOutput, variables: LoginAPIInput, context: unknown): void => {
    queryClient.invalidateQueries('user');
    queryClient.setQueryData('user', data);
    const dehydratedState = dehydrate(queryClient);
    sessionStorage.setItem('user', JSON.stringify(dehydratedState));
  }
  
   /**
   * 로그인 과정에서 오류가 발생하면 호출되는 함수
   * @param {AxiosError} error - 발생한 에러
   * @param {LoginAPIInput} variables - 로그인 API의 입력 데이터
   * @param {unknown} context - 알 수 없는 컨텍스트 데이터
   */
  const handleError = (error: AxiosError, variables: LoginAPIInput, context: unknown): void => {
    console.log('Mutation Error: ', error);
  }

  /**
   * 사용자 로그인을 위한 API 호출 함수
   * @param {LoginAPIInput} loginInput - 로그인 정보
   * @return {Promise<any>} 응답 데이터
   */
  const loginAPI = async (loginInput: LoginAPIInput) => {
    try {
      const res = await userLogin(loginInput);
      
      if (res.status === 200) {
        await Swal.fire({
          title: t('common:Success'),
          text: res.data.message,
          icon: 'success',
          confirmButtonText: 'OK',
          confirmButtonColor: '#6BCB77'
        });
        router.push('/');
      } else {
        await Swal.fire({
          title: t('common:Error'),
          text: res.data.message,
          icon: 'error',
          confirmButtonText: 'OK',
          confirmButtonColor: '#6BCB77'
        });
        throw new Error(res.data.message);
      }
  
      return res.data.data;
    } catch (error) {
      const err = error as AxiosError;

      const data = err.response?.data as { message: string };

      // 400 에러 처리
      if (err.response?.status === 400) {
        console.error("400 error detected. Session storage won't be updated.");
      } else {
        dispatch(showErrorAlert(data?.message));
      }

      throw error;
    } finally {
      Swal.close();
    }
  };

  /**
   * 로그인 API를 호출하기 위한 useMutation 훅
   */
  const loginMutation = useMutation(loginAPI, {
    onSuccess: handleLoginSuccess,
    onError: handleError
  });

  
  /**
   * 로그인 실행 함수
   */
  const login = () => {
    loginMutation.mutate({ email, password });
  };
```
*로그인 코드*

`useMutation`은 **POST** 역할을 해준다. `useMutation` Hook으로 수행되는 Mutation 요청은 HTTP Method **POST, PUT, DELETE** 요청과 같이 서버에 Side Effect를 발생시켜 서버의 상태를 변경시킬 때 사용한다.  
`useMutation`의 첫 번째 파라미터는 이 **Mutation 요청을 수행하기 위한 Promise를 Return하는 함수**이며, useMutation의 return 값 중 mutate (또는 mutateAsync) 함수를 호출하여 서버에 Side Effect를 발생시킬 수 있다.  
`onSuccess` 옵션을 이용해 **POST 통신이 완료되면** `queryClient`를 사용하여 `user`라는 쿼리를 무효화하고, 로그인 API 응답 데이터로 `user` 쿼리 데이터를 설정한다. 그리고 쿼리 데이터를 세션 스토리지에 저장한다.
`onError` 옵션은 `Mutation Error`를 콘솔에 출력한다.  

### Notice, General 게시글 리스트
{:toc}

![공지사항 리스트](../../assets/img/codestates/cleanmile/notice.png){: width="550" height="550"} | ![자유 게시글 리스트](../../assets/img/codestates/cleanmile/general.png){: width="550" height="550"}

*공지사항, 자유 게시글 리스트*

공지사항과 자유 게시글 리스트의 경우 일반 `Table`형식으로 구현했다. 해당 게시판은 이미지가 필수로 들어가지 않으며 많은 글이 올라올 수 있기에 이러한 형식으로 구현했다.  
현재 페이지 번호를 url에 담으면 서버에서 게시글 리스트를 최대 10개씩 잘라서 반환해준다. 필터링 또한 같은 방식으로 필터가 변경되면 `option`의 `value`값을 url에 담으면 서버에서 해당 `value`에 따라 게시글을 필터링하여 게시글 리스트를 반환한다.  
처음에는 서버에 `params`로 데이터를 보내주거나 반환받는 형식이 익숙치 않아 조금 헤맸지만 한 번 해보니 생각보다 어렵지 않았다. 나는 `router.push`를 사용하여 url을 변경했는데 원래 이런 식으로 페이지네이션이나 필터링, 검색을 처리하는지는 잘 모르겠다. 코드에 정답은 없다고는 하나 괜찮은 방법인지는 모르겠다.  
공지사항과 자유 게시글 등 게시글 리스트 페이지들은 데이터를 생성하거나 변경하는 사항이 없어 SSR을 사용하여 렌더링되도록 구현했다.

```tsx
  /**
   * 사용자가 현재 있는 페이지를 나타냄
   * 라우터의 쿼리에서 페이지를 가져오거나 기본 페이지 상수를 기본값으로 사용
   * @type {number}
   */
  const [currentPage, setCurrentPage] = useState(
    Number(router.query.page) || DEFAULT_PAGE
  );

 /**
   * 게시글 페이징을 기반으로 사용 가능한 총 페이지 수
   * @type {number}
   */
  const totalPages = postPagination?.totalPages;

  /**
   * 페이지 변경 이벤트 처리
   * 주어진 페이지 번호로 현재 페이지를 설정
   * @param {number} pageNumber - 새 페이지 번호
   */
  const handlePageChange = (pageNumber: number) => {
    setCurrentPage(pageNumber);
  };

 /**
   * 현재 페이지가 변경될 때마다 히스토리에 새 경로를 푸시함
   */
  useEffect(() => {
    router.push(`/posts/general?page=${currentPage}`);
  }, [currentPage]);

 return (
  <div className='w-full mt-16 sm:mt-10 xs:mt-5 mb-5 flex justify-center'>
   <div className='flex items-center'>
    {Array.from({ length: totalPages }, (_, i) => (
     <button
      key={i + 1}
      className={`px-2 py-2 mx-1 xs:text-sm ${currentPage === i + 1 ? 'font-bold' : ''
       }`}
      onClick={() => handlePageChange(i + 1)}
     >
      {i + 1}
     </button>
    ))}
   </div>
  </div>
 )
```

*페이지네이션 코드*  

```tsx
  /**
   * 페이지 변경 이벤트 처리
   * 주어진 페이지 번호로 현재 페이지를 설정
   * @param {number} pageNumber - 새 페이지 번호
   */
  const handlePageChange = (pageNumber: number) => {
    setCurrentPage(pageNumber);
  };

  /**
   * 필터 변경을 처리
   * 선택한 순서에 따라 해당 URL로 리디렉션
   * @param {React.ChangeEvent<HTMLSelectElement>} e - 선택 요소의 변경으로 트리거된 이벤트
   */
  const handleFilterChange = (e: React.ChangeEvent<HTMLSelectElement>) => {
    const order = e.target.value;
    router.push(`/posts/general?page=${currentPage}&order=${order}`);
  };

 return (
  <select className='border border-black py-2 px-4 pr-7 rounded-md text-sm'
   onChange={handleFilterChange}>
   <option className='text-sm xs:text-xs' value='desc'>
    {t('common:Latest order')}
   </option>
   <option className='text-sm xs:text-xs' value='asc'>
    {t('common:Old order')}
   </option>
   <option className='text-sm xs:text-xs' value='view'>
    {t('common:View order')}
   </option>
  </select>
 )
```

*필터링 코드*

```tsx
export const getServerSideProps = async (
  context: GetServerSidePropsContext
) => {
  const { query } = context;
  const page = query.page ? query.page : '1';
  const order = query.order ? query.order : 'desc';
  const title = query.title ? query.title : null;
  const content = query.content ? query.content : null;

  try {
    let URL;
    if (title) {
      URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/lists/general?page=${page}&order=${order}&title=${title}`;
    } else if (content) {
      URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/lists/general?page=${page}&order=${order}&content=${content}`;
    } else {
      URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/lists/general?page=${page}&order=${order}`;
    }
    const dataBody = null;
    const headers = {};
    const isJSON = false;
    const isCookie = true;

    const res = await ApiCaller.get(URL, dataBody, isJSON, headers, isCookie);

    let postList;
    let postPagination;
    if (res.status === 200 && res.data.success) {
      postList = res.data.data.data;
      postPagination = res.data.data.pagination;
    } else {
      // API 호출에 실패하면 오류 메시지를 출력하고 빈 객체를 반환합니다.
      console.error('API 호출 실패:', res.data.message);
      postList = {};
      postPagination = {};
    }
    return { props: { postList, postPagination } };
  } catch (error) {
    console.error('게시글 리스트를 가져오는데 실패했습니다:', error);

    return {
      props: {
        postList: null,
        postPagination: null,
      },
    };
  }
};

```

*게시글 리스트 SSR 코드*
> 공지사항과 자유 게시글 SSR 코드는 비슷하여 이 중 하나만 블로그에 작성했습니다.

### Event, Review 게시글 리스트
{:toc}

![이벤트 리스트](../../assets/img/codestates/cleanmile/event.png){: width="550" height="550"} | ![리뷰 리스트](../../assets/img/codestates/cleanmile/review.png){: width="550" height="550"}

*이벤트, 리뷰 게시글 리스트*

이벤트와 리뷰 게시글 리스트는 카드 형식으로 무한 스크롤을 사용하여 구현했다. 해당 게시판은 포스터나, 후기 이미지 등 이미지가 거의 필수적으로 들어간다고 생각하여 직관적으로 보이는 것이 좋다고 생각하여 이러한 형식으로 구현했다.  
무한 스크롤의 경우 백엔드에서 이벤트나 리뷰 게시글의 마지막 `ID`를 반환해주면 그 `ID`를 체크하여 페이지가 마지막 요소까지 도달했는지 확인한다. 만약 스크롤이 마지막 요소에 도달했고, 다음 페이지의 데이터가 잇을 경우 함수를 호출하여 다음 페이지의 데이터를 가져온다.  
사실 이 무한 스크롤에서 꽤나 헤맸었다. Chat GPT를 이용해 코드를 물어보고 예제 코드를 봐도 이해가 잘 가지 않았다. 게다가 중복된 데이터를 계속 불러오는데 이유도 모르겠고, 그냥 막막한 기분이 들어서 포기할까 했었다.  
그래도 계속 GPT한테 꼬리 물기로 질문을 하면서 해결을 했는데, 알고보니 마지막 게시글 `Id`가 제대로 전달이 안되는 문제가 있었던 것이다. 그래서 데이터가 없을 때의 예외 처리를 하고 컴포넌트 부분에 추가하니 정상적으로 데이터가 불러와지는 것을 확인할 수 있었다.

```tsx
/**
 * 라우터 쿼리를 기반으로 검색 유형과 검색어를 파악
 */
const searchType = router.query.title ? 'title' : router.query.content ? 'content' : null;
const searchTerm = searchType ? router.query[searchType] as string : '';

/**
   * 무한 쿼리를 사용하여 이벤트 데이터를 가져옴
   */
  const {
    data,
    fetchNextPage,
    hasNextPage,
    isLoading,
    isFetchingNextPage,
    refetch
  } = useInfiniteQuery('events',
    ({ pageParam }) => fetchEventsWithPaging({
      pageParam: pageParam,
      title: searchType === 'title' ? searchTerm : undefined,
      content: searchType === 'content' ? searchTerm : undefined,
      filter: filter === 'all' ? undefined : filter,
    } as FetchEventParams),
    {
      getNextPageParam: (lastPage) => lastPage.last_id,
      enabled: true
    }
  );

  /**
   * 필터나 검색어가 변경될 때마다 데이터를 다시 가져옴
   */
  useEffect(() => {
    refetch();
  }, [searchTerm, searchType, filter, refetch]);

  /**
   * 무한 스크롤 로직을 위한 IntersectionObserver를 설정
   */
  const observer = useRef<IntersectionObserver | null>();
  const lastElementRef = useCallback(
    (node: HTMLElement | null) => {
      if (isLoading || isFetchingNextPage) return;
      if (observer.current) observer.current.disconnect();

      observer.current = new IntersectionObserver(entries => {
        if (entries[0].isIntersecting && hasNextPage) {
          fetchNextPage();
        }
      });

      if (node) observer.current.observe(node);
    },
    [isLoading, isFetchingNextPage, hasNextPage, fetchNextPage]  // 의존성 업데이트
  );

  /**
   * 어떤 페이지라도 데이터가 있는지 여부를 확인
   * @type {boolean}
   */
  const hasData = data?.pages.some(page => page.data?.length > 0);

  /**
   * 드롭다운에서 필터 값을 변경할 때의 핸들러 함수
   * @param {React.ChangeEvent<HTMLSelectElement>} e - 선택 이벤트 객체
   */
  const handleFilterChange = (e: React.ChangeEvent<HTMLSelectElement>) => {
    const selectedValue = e.target.value;
    setFilter(selectedValue === 'all' ? undefined : selectedValue);
  };
```

*무한 스크롤 코드*

```tsx
export const getServerSideProps = async (context: GetServerSidePropsContext) => {
  const { query } = context;
  const last_id = query.page ? query.page as string : 'null';
  const title = query.title ? query.title as string: null;
  const content = query.content ? query.content as string : null;
  const status = query.status ? query.status as string : null;

  try {
    const params = new URLSearchParams();
    if (title) params.append('title', title);
    if (content) params.append('content', content);
    if (status) params.append('status', status);
    if (last_id) params.append('last_id', last_id);
    
    const URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/events/list?${params.toString()}`;

    const dataBody = null;
    const headers = {};
    const isJSON = false;
    const isCookie = true;

    const res = await ApiCaller.get(URL, dataBody, isJSON, headers, isCookie);

    let eventList;
    let lastId;
    if (res.status === 200 && res.data.success) {
      eventList = res.data.data.data;
      lastId = res.data.data.last_id;
    } else {
      // API 호출에 실패하면 오류 메시지를 출력하고 빈 객체를 반환합니다.
      console.error('API 호출 실패:', res.data.message);
      eventList = {};
      lastId = '';
    }
    return { props: { eventList, lastId } };
  } catch (error) {
    console.error('이벤트 리스트를 가져오는데 실패했습니다:', error);

    return {
      props: {
        eventList: null,
        lastId: null,
      }
    };
  }
}
```
*게시글 리스트 코드*
> 이벤트와 리뷰 게시글 코드는 비슷하여 하나만 블로그에 작성했습니다.

`useInfiniteQuery`는 `React Query`에서 제공하는 훅이다. 이 훅은 페이지네이션과 관련된 데이터를 가져올 때 유용하게 사용된다. 이벤트 데이터는 `fetchEventsWithPaging` 함수를 통해 가져오고, 이 함수에는 페이지 정보, 검색 타입 및 필터와 관련된 파라미터들이 전달된다. `getNextPageParam`은 다음 페이지를 가져오기 위한 파라미터를 지정하는데, 여기서는 `lastPage.last_id`를 사용하여 마지막 페이지의 `ID`를 가져온다.

- `data`
  - 쿼리를 통해 가져온 데이터
  - `useInfiniteQuery`를 사용할 때, `data`는 페이지화된 데이터의 배열을 포함한다. 즉, 각 페이지의 결과는 배열 내의 별도의 항목으로 저장된다.
- `fetchNextPage`
  - 다음 페이지의 데이터를 명시적으로 가져오는 함수
  - 무한 스크롤에서 사용자가 페이지의 끝에 도달하면 이 함수를 호출하여 다음 페이지의 데이터를 불러온다.
- `hasNextPage`
  - 다음 페이지의 데이터가 있는지 여부를 나타내는 `boolean` 값
  - 이 값을 통해 추가로 더 로드할 페이지가 있는지 알 수 있으며, `fetchNextPage` 함수의 호출 여부를 결정한다.
- `isLoading`
  - 쿼리가 초기 데이터 로딩 중인지 나타내는 `boolean` 값
  - 첫 페이지의 데이터를 처음 로드할 때 이 값이 `true`가 된다.
- `isFetchingNextPage`
  - 다음 페이지의 데이터를 로딩 중인지 여부를 나타내는 `boolean` 값
  - `fetchNextPage` 함수가 호출되어 다음 페이지의 데이터를 로딩 중일 때, 이 값은 `true`가 된다.
- `refetch`
  - 쿼리를 강제로 다시 가져오는 함수
  - 어떤 이유로든 데이터를 새고로침하거나 다시 가져와야 할 때 이 함수를 사용한다.
  - 나의 경우에는 검색이나 필터링을 하기 위해 사용했다.

`IntersectionObserver`는 타겟 요소와 그 부모 요소나 최상위 `document`의 `viewport`사이의 교차점을 비동기적으로 관찰하는 방법을 제공한다. `observer`라는 이름의 `useRef`훅을 사용하여 `IntersectionObserver`의 인스턴스를 참조한다. `lastElementRef`는 콜백 함수로, 페이지의 마지막 요소에 바인딩된다. 이 함수는 스크롤이 마지막 요소까지 도달했는지 관찰한다. 만약 스크롤이 마지막 요소에 도달했고, 다음 페이지의 데이터가 있을 경우 (`hasNextPage`가 `true`일 경우) `fetchNextPage` 함수를 호출하여 다음 페이지의 데이터를 가져온다.

### 게시글 상세 페이지
{:toc}

![공지사항 상세 페이지](../../assets/img/codestates/cleanmile/notice_detail.png){: width="550" height="550"} | ![자유 게시글 상세 페이지](../../assets/img/codestates/cleanmile/general_detail.png){: width="550" height="550"}  
![리뷰 게시글 상세 페이지](../../assets/img/codestates/cleanmile/review_detail.png){: width="550" height="550"} | ![이벤트 상세 페이지](../../assets/img/codestates/cleanmile/event_detail.png){: width="550" height="550"}

*게시글 상세 페이지*

![게시글 작성자인 경우](../../assets/img/codestates/cleanmile/general_detail_writer.png){:.centered}

*게시글 작성자인 경우 버튼 표시*

게시글 상세 페이지 또한 SSR을 사용했다. 게시글의 작성자인 경우 삭제와 수정 버튼이 보이며, 삭제나 수정이 가능하다.  
이벤트의 경우에는 이벤트에 참여한 유저인 경우 `신청` 버튼 대신 `참여 완료`가 보이며 클릭이 불가능하도록 구현했다. 또한 로그인한 유저가 아닌 경우에도 `신청` 버튼 클릭은 불가능하다.  
게시글 작성자의 닉네임을 클릭하면 작성자의 페이지로 이동할 수 있는데, 작성자 본인인 경우 마이 페이지로, 다른 유저의 경우 해당 유저의 페이지로 이동한다. 만약 탈퇴하여 DB에 존재하지 않는 유저인 경우 닉네임은 `알수없음`으로 표기되며 해당 유저의 페이지로 이동도 불가능하도록 구현했다.

```tsx
  /**
   * 사용자 로그인 상태를 상태로 관리
   * @type {boolean}
   */
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  /**
   * 컴포넌트 마운트 시, 세션 스토리지에서 사용자 로그인 정보를 가져와 상태를 설정
   */
  useEffect(() => {
    setIsLoggedIn(Boolean(sessionStorage.getItem('user')));
  }, []);
```

*로그인 상태 확인 코드*

```tsx
/**
   * 사용자 프로필 페이지로 이동하는 함수
   * 게시물 작성자의 프로필을 확인하거나, 자신의 프로필 페이지로 리디렉션
   */
  const handleProfile = () => {
    if (postDetail.user_id === null) {
      dispatch(showErrorAlert(t('common:User does not exist')));
    } else {
      if (postDetail.user_id._id === userData?.user._id) {
        router.push(`/users/mypage`)
      } else {
        router.push(`/users/profile?id=${postDetail.user_id._id}`)
      }
    }
  }

```

*유저 페이지로 이동하는 코드*

```tsx
  /**
   * 게시물 삭제를 확인하는 함수
   * SweetAlert2를 사용하여 사용자에게 삭제를 확인하는 팝업을 표시
   * @returns {Promise<SweetAlertResult<any>>} 삭제를 진행할지 또는 취소할지에 대한 사용자의 결정.
   */
  const confirmDelete = () => {
    return Swal.fire({
      title: t('common:Are you sure you want to delete it'),
      icon: 'question',
      showCancelButton: true,
      confirmButtonText: 'OK',
      confirmButtonColor: '#6BCB77',
      cancelButtonText: t('common:Cancel'),
      cancelButtonColor: '#FF6B6B'
    });
  }

  /**
   * 실제로 게시물을 삭제하는 함수
   * @returns {Promise<any>} 삭제 응답 데이터.
   */
  const performDelete = async () => {
    const res = await userPostDelete(postDetail._id);

    if (res.status === 200) {
      dispatch(showSuccessAlert(res.data.message));
      router.replace('/posts/general');
    } else {
      dispatch(showErrorAlert(res.data.message));
    }

    return res.data.data;
  }

  /**
   * 게시물 삭제를 처리하는 함수
   * 삭제를 확인한 후 실제 삭제를 수행하고, 그 결과에 따라 알림을 표시 
   */
  const postDelete = async () => {
    const result = await confirmDelete();

    if (result.isConfirmed) {
      try {
        await performDelete();
      } catch (error) {
        const err = error as AxiosError;

        const data = err.response?.data as { message: string };

        dispatch(showErrorAlert(data?.message));
      }
    } else if (result.isDismissed) {
      dispatch(showSuccessAlert(t('common:You have cancelled deleting the post')));
    }
  }

```

*게시글 삭제 코드*

```tsx
{isLoggedIn && userData?.user._id === postDetail.user_id?._id ? (
 <>
  <button className='
   w-[5%]
   lg:w-[15%]
   md:w-[15%]
   sm:w-[25%]
   xs:w-[30%] 
   border 
   rounded-2xl 
   xs:rounded-lg
   p-3
   sm:p-2 
   xs:p-1
   bg-main-red 
   text-white 
   xs:text-sm
   hover:bg-red-500 
   transition 
   duration-300
   text-center'
   onClick={postDelete}>
   {t('common:Delete')}
  </button>
  <Link
   href={`/posts/general/edit/${postDetail._id}`}
   className='
    w-[5%]
    lg:w-[15%]
    md:w-[15%]
    sm:w-[25%]
    xs:w-[30%] 
    border 
    rounded-2xl 
    xs:rounded-lg
    p-3
    sm:p-2 
    xs:p-1
    bg-main-blue 
    text-white 
    xs:text-sm
    hover:bg-blue-600 
    transition 
    duration-300
    text-center'>
   <button>
    {t('common:Edit')}
   </button>
  </Link>
  <Link href='/posts/general?page=1'
   className='
   w-[5%]
   lg:w-[15%]
   md:w-[15%]
   sm:w-[25%]
   xs:w-[30%] 
   border 
   rounded-2xl 
   xs:rounded-lg
   p-3
   sm:p-2 
   xs:p-1
   bg-main-green 
   text-white 
   xs:text-sm
   hover:bg-green-600 
   transition 
   duration-300
   text-center'>
   <button>
    {t('common:List')}
   </button>
  </Link>
 </>
) : (
 <Link href='/posts/general?page=1'
  className='
  w-[5%]
  lg:w-[15%]
  md:w-[15%]
  sm:w-[25%]
  xs:w-[30%] 
  border 
  rounded-2xl 
  xs:rounded-lg
  p-3
  sm:p-2 
  xs:p-1
  bg-main-green 
  text-white 
  xs:text-sm
  hover:bg-green-600 
  transition 
  duration-300
  text-center'>
  <button>
   {t('common:List')}
  </button>
 </Link>
)}
```

*게시글 작성자 확인 코드*

```tsx
export const getServerSideProps = async (context: GetServerSidePropsContext) => {
  const { pid } = context.query;

  const URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/detail/${pid}`;
  const dataBody = null;
  const headers = {};
  const isJSON = false;
  const isCookie = false;

  const res = await ApiCaller.get(URL, dataBody, isJSON, headers, isCookie);

  let noticeDetail;
  let comments;
  if (res.status === 200 && res.data.success) {
    noticeDetail = res.data.data.post;
    comments = res.data.data.comment;
  } else {
    // API 호출에 실패하면 오류 메시지를 출력하고 빈 객체를 반환
    console.error('API 호출 실패:', res.data.message);
    noticeDetail = null;
    comments = null;
  }



  // 이 데이터를 페이지의 props로 반환
  return { props: { noticeDetail, comments } };
}
```
*공지사항 상세 페이지 SSR 코드*
> 상세 페이지의 SSR 코드는 공지사항, 자유, 리뷰, 이벤트 모두 비슷하여 이 중 하나의 코드만 블로그에 작성했습니다.

### 게시글 작성
{:toc}

![자유 게시글 작성 페이지](../../assets/img/codestates/cleanmile/post_create.png){: width="550" height="550"} | ![리뷰 게시글 작성 페이지](../../assets/img/codestates/cleanmile/review_create.png){: width="550" height="550"}

*자유, 리뷰 게시글 작성 페이지*

게시글 작성은 카테고리를 선택할 수 있는데, 리뷰를 선택하는 경우 유저가 참여한 이벤트 리스트가 카테고리 옆에 `select`로 선택할 수 있도록 구현했다.  
리뷰 게시글은 이벤트가 종료되어야 가능하다.  

```tsx
const [selectCategory, setSelectCategory] = useState('');
const [title, setTitle] = useState('');
const [content, setContent] = useState('');
const [images, setImages] = useState<IFile[]>([]);
const [videos, setVideos] = useState<IFile[]>([]);
const [selectedFile, setSelectedFile] = useState<IFile[]>([]);
const [isReview, setIsReview] = useState(false);
const [selectEvent, setSelectEvent] = useState('');

/**
   * 사용자 데이터를 기반으로 첫 번째 이벤트를 선택
   */
  useEffect(() => {
    if (userData?.events && userData?.events.length > 0) {
      setSelectEvent(userData?.events[0]._id);
    }
  }, [userData?.events]);

  const fileInputRef = useRef<HTMLInputElement>(null);

  /**
   * 파일 선택을 위한 인풋을 트리거함
   */
  const handleFileSelect = useCallback(() => {
    fileInputRef.current?.click();
  }, []);

  /**
   * 카테고리 선택 변경을 처리하는 함수
   * @param {React.ChangeEvent<HTMLSelectElement>} e - 카테고리 변경 이벤트 객체
   */
  const handleCategoryChange = (e: React.ChangeEvent<HTMLSelectElement>) => {
    const selectedCategory = e.target.value;
    setSelectCategory(selectedCategory);
    setIsReview(selectedCategory === 'review');
  }

  /**
   * 사용자가 파일을 선택하면 이를 처리하는 함수
   * 이 함수는 선택한 파일의 확장자를 확인하고,
   * 확장자에 따라 이미지 또는 비디오를 각각의 상태에 저장
   * @param {Event} e - 파일 입력 이벤트 객체
   */
  const handleFileChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const files: IFile[] = Array.from(e.target.files!) as IFile[];

    files.forEach((file) => {
      const extension = file.name.split('.').pop()?.toLowerCase();

      if (['jpg', 'jpeg', 'png'].includes(extension || '')) {
        setImages((prevImages) => [...prevImages, file]);
      } else if (['mp4', 'avi', 'mov'].includes(extension || '')) {
        setVideos((prevVideos) => [...prevVideos, file]);
      }
    });
    setSelectedFile(files)
  };

  /**
   * 새로운 게시물을 생성하는 함수
   */
  const createPost = async () => {
    try {
      const res = await userCreatePost(selectCategory, title, content, selectEvent, images, videos);
      if (res.status === 200) {
        await Swal.fire({
          title: 'Success',
          text: res.data.message,
          icon: 'success',
          confirmButtonText: 'OK',
          confirmButtonColor: '#6BCB77'
        });
        router.push(`/users/mypage`);
      } else {
        dispatch(showErrorAlert(res.data.message));
      }
    } catch (error) {
      const err = error as AxiosError;

      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }
```

*게시글 생성 코드*

### 게시글 수정
{:toc}

![자유 게시글 수정 페이지](../../assets/img/codestates/cleanmile/post_edit.png){: width="550" height="550"} | ![리뷰 게시글 수정 페이지](../../assets/img/codestates/cleanmile/review_edit.png){: width="550" height="550"}

*자유, 리뷰 게시글 수정 페이지*

게시글 수정은 한 번 작성한 카테고리에서 다른 카테고리로 수정이 안되도록 구현했다. 우리 서비스의 경우 게시글 작성 시에 이미지를 첨부했을 때 다른 이미지로 수정이 불가능하다. 따라서 리뷰 게시글이나 자유 게시글에 첨부한 이미지가 있을 경우 해당 이미지가 삭제나 변경이 불가하여 카테고리 수정이 안되도록 구현했다. 

```tsx
  const [selectCategory, setSelectCategory] = useState('');
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');
  const [images, setImages] = useState<IFile[]>([]);
  const [videos, setVideos] = useState<IFile[]>([]);
  const [selectedFile, setSelectedFile] = useState<IFile[]>([]);

  /**
   * 파일을 선택할 수 있도록 input 요소의 참조를 생성
   * @type {RefObject<HTMLInputElement>}
   */
  const fileInputRef = useRef<HTMLInputElement>(null);

  /**
   * 파일 입력 요소를 클릭하여 사용자가 파일을 선택할 수 있도록 함
   */
  const handleFileSelect = () => {
    fileInputRef.current?.click();
  };

  /**
   * 사용자가 파일을 선택했을 때 해당 파일의 확장자를 확인하고 
   * 해당 확장자에 따라 이미지 또는 비디오 상태를 업데이트하는 함수
   * @param {React.ChangeEvent<HTMLInputElement>} e - 파일을 선택했을 때 발생하는 이벤트 객체
   */
  const handleFileChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const files: IFile[] = Array.from(e.target.files!) as IFile[];

    files.forEach((file) => {
      const extension = file.name.split('.').pop()?.toLowerCase();

      if (['jpg', 'jpeg', 'png'].includes(extension || '')) {
        setImages((prevImages) => [...prevImages, file]);
      } else if (['mp4', 'avi', 'mov'].includes(extension || '')) {
        setVideos((prevVideos) => [...prevVideos, file]);
      }
    });
    setSelectedFile(files)
  };

  /**
   * 게시물을 수정하고 수정된 게시물의 ID를 반환하는 함수
   * 성공적으로 게시물이 수정되면 수정된 게시물 페이지로 리디렉션
   */
  const editPost = async () => {
    try {
      const updatedPostId = await updatePost(postDetailDefault._id, title, content, images, videos);
      dispatch(showSuccessAlert(t('Success')));
      router.replace(`/posts/review/${updatedPostId}`);
    } catch (error) {
      const err = error as AxiosError;

      const data = err.response?.data as { message: string };

      dispatch(showErrorAlert(data?.message));
    }
  }

return (
 <select className="
  border-b 
  outline-none 
  focus:border-black 
  transition 
  duration-300 
  py-2 
  px-4 
  w-full
  sm:text-sm
  xs:text-sm"
  value={selectCategory}
  onChange={(e) => setSelectCategory(e.target.value)}
  required>
  <option className="text-sm" defaultValue="general" selected>{t('common:General')}</option>
 </select>
)
```

*게시글 수정 코드*
> 자유, 리뷰 게시글 수정 코드는 비슷하여 이 중 하나만 블로그에 작성했습니다.

### 유저 페이지
{:toc}

![마이 페이지](../../assets/img/codestates/cleanmile/mypage.png){: width="550" height="550"} | ![유저 페이지](../../assets/img/codestates/cleanmile/userpage.png){: width="550" height="550"}

*마이페이지, 유저 페이지*

로그인한 유저 본인의 마이페이지에서는 유저가 참여한 이벤트 리스트와 작성한 게시글 리스트, 참여 인증 후 받은 배지를 확인할 수 있다. 또한 닉네임과 배너 수정이 가능한 수정 버튼이 있고, `DNFT Upgrade`, `Mileage Exchange`, `QR Code Scan` 버튼을 확인할 수 있다. 우리 서비스는 회원가입을 하면 **DNFT**를 발급해주는데, 이 DNFT는 유저의 프로필 사진으로 확인할 수 있다. `DNFT Upgrade` 버튼은 유저의 배지 점수에 따라 이 DNFT를 업그레이드 할 수 있다. 업그레이드를 진행하면 프로필 이미지는 단계에 따른 이미지로 변경이 된다.  
`Mileage Exchange` 버튼은 유저가 리뷰 작성이나 커뮤니티 활동을 하면서 받은 마일리지를 토큰으로 교환할 수 있는 버튼이다. 마일리지 1개당 토큰 1개이며, 마일리지가 5개 이상 있어야 교환이 가능하다. 아직 우리 서비스에는 토큰으로 무언가를 할 수 없으나 향후 서비스를 확장할 때 토큰을 활용할 수 있는 마켓 플레이스를 구축할 예정이다.  
로그인한 유저가 아닌 유저의 페이지는 이벤트 참여 인증 시 받은 배지와 작성한 게시글 리스트, 프로필 이미지, 지갑 주소, 닉네임, 배너 이미지 등을 확인할 수 있다. 로그인한 유저가 아니기 때문에 프로필 수정 버튼은 없으며 참여한 이벤트 리스트는 이벤트 참여 인증 시 받은 배지가 있어 따로 보여주지는 않도록 구현했다.  
배지는 유저가 이벤트에 참여 후 인증을 하면 받을 수 있는데, 이벤트 참여 신청 후 이벤트 현장에서 주최 측이 게시한 QR코드를 스캔하면 이벤트 참여 인증이 가능하다. QR 코드 스캔은 마이페이지에서 `QR Code Scan` 버튼을 클릭하면 스캔할 수 있는 페이지로 이동한다. QR 코드를 스캔하는 즉시 이벤트 배지를 발급받을 수 있다. 배지는 **ERC-1155**로 발급되어 유저가 회원가입 시 연결한 메타마스크 지갑으로 전송된다. 배지는 이벤트마다 등급이 정해져 있으며, 점수도 등급마다 정해져 있다.

> 배지 점수 정책
> 1단계(씨앗) : 0점(회원가입 상태)~ 14점 (간격: 15점)
> 2단계(새싹) : 15점 ~ 39점 (간격25점)
> 3단계(잎새) : 41점 ~ 74점 (간격35점)
> 4단계(가지) : 75점 ~ 119점 (간격45점)
> 5단계(열매) : 120점

```tsx
const [fileUrl, setFileUrl] = useState<string | null>(null);
const [uploadFile, setUploadFile] = useState<File | null>(null);
const [isEditing, setIsEditing] = useState(false);
const [nickname, setNickname] = useState(userInfo?.nickname);
const [errorMessage, setErrorMessage] = useState('');

/**
 * 파일 업로드 이벤트를 처리
 * @param {Event} e - 파일 업로드 이벤트
 * @returns {void}
 */
const fileUpload = (e: React.ChangeEvent<HTMLInputElement>) => {
 if (e.target.files) {
  const FILE = e.target.files[0];
  const TYPE = (FILE.type).split('/')[1];
  const FSIZE = (FILE.size) / Math.pow(10, 6);

  if (FSIZE < MAX_FILE_SIZE) {
   EXTENSIONS.forEach(e => {
    if (e.type === TYPE) {
     const objectURL = URL.createObjectURL(FILE);
     setFileUrl(objectURL);
     setUploadFile(FILE);
    }
   });
  }
 }
}

/**
 * 마이 페이지 수정 상태로 전환하는 함수
 */
const myPageEdit = () => {
 setIsEditing(true);
};

/**
 * 닉네임을 유효성 검사하는 함수
 * 입력한 닉네임이 유효한지 확인하고, 유효하지 않은 경우 에러 메시지를 설정 
 */
const validateNickname = () => {
 if (nickname?.length < 2) {
  setErrorMessage(`닉네임은 최소 ${MIN_LENGTH}자 이상이어야 합니다.`);
 } else if (nickname?.length > 8) {
  setErrorMessage(`닉네임은 최대 ${MAX_LENGTH}자 입니다.`);
 } else {
  setErrorMessage('');
 }
};

useEffect(() => {
 validateNickname();
}, [nickname]);

/**
 * 프로필 정보 변경 함수
 * 닉네임과 이미지 변경 여부를 확인하여 해당 정보를 업데이트
 */
const profileChange = async () => {
 const hasNicknameChange = nickname !== userInfo.nickname;
 const hasImageChange = uploadFile !== null;

 try {
  if (hasNicknameChange) {
   const res = await changeUserNickname(nickname);
   handleResponse(res, 'nickname', nickname);
  }

  if (hasImageChange) {
   const res = await changeUserBanner(uploadFile);
   console.log(res.data)
   handleResponse(res, 'banner_img_url', res.data.imageUrl);
  }
 } catch (error) {
  const err = error as AxiosError;
  const data = err.response?.data as { message: string };
  dispatch(showErrorAlert(data?.message));
 }
};

/**
 * API 응답 처리 함수
 * @param {AxiosResponse} res - Axios로부터 받은 응답
 * @param {'nickname' | 'banner_img_url'} type - 변경하려는 사용자 정보 유형
 * @param {string} value - 변경하려는 값
 */
const handleResponse = (res: AxiosResponse, type: 'nickname' | 'banner_img_url', value: string) => {
 if (res.status === 200) {
  dispatch(showSuccessAlert(t('common:Profile change was successful')))
  if (type === 'nickname') {
   setLocalUserInfo((prev) => ({ ...prev, nickname: value }));
  } else if (type === 'banner_img_url') {
   setLocalUserInfo((prev) => ({ ...prev, banner_img_url: value }));
  }
  setIsEditing(false);
 } else {
  dispatch(showErrorAlert(res.data.message));
 }
}
```

*프로필 변경 코드*

```tsx
/**
 * DNFT 업그레이드 함수
 */
const upgradeDnft = async () => {
 Swal.fire({
  title: t('common:Upgrading'),
  allowOutsideClick: false,
  didOpen: () => {
   Swal.showLoading();
  }
 });

 try {
  const res = await upgradeUserDnft();

  Swal.close();

  if (res.status === 200) {
   dispatch(showSuccessAlert(res.data?.message));
   router.reload();
  } else {
   dispatch(showErrorAlert(res.data?.message));
  }
 } catch (error) {
  Swal.close();

  const err = error as AxiosError;
  const data = err.response?.data as { message: string };
  dispatch(showErrorAlert(data?.message));
 }
};
```
*DNFT 업그레이드 코드*

```tsx
/**
 * 마일리지를 토큰으로 교환하는 함수
 */
const tokenExchange = async () => {
 try {
  const res = await exchangeToken(userInfo._id);
  if (res.status === 200) {
   dispatch(showSuccessAlert(res.data?.message));
  } else {
   dispatch(showErrorAlert(res.data?.message));
  }
 } catch (error) {
  const err = error as AxiosError;
  const data = err.response?.data as { message: string };
  dispatch(showErrorAlert(data?.message));
 }
};
```
*마일리지를 토큰으로 교환하는 코드*


```tsx
export const getServerSideProps = async (
  context: GetServerSidePropsContext
) => {
  const cookiesObj = cookie.parse(context.req.headers.cookie || '');

  if (!cookiesObj.clientAccessToken) {
    return {
      redirect: {
        destination: '/login',
        permanent: false,
      },
    }
  }

  let cookiesStr = '';
  if (context.req && cookiesObj) {
    cookiesStr = Object.entries(cookiesObj)
      .map(([key, value]) => `${key}=${value}`)
      .join('; ');
    axios.defaults.headers.Cookie = cookiesStr;
  }

  try {
    const URL = `${process.env.NEXT_PUBLIC_BACKEND_URL}/users/profile`;
    const dataBody = null;
    const headers = {};
    const isJSON = false;
    const isCookie = true;

    const res = await ApiCaller.get(URL, dataBody, isJSON, headers, isCookie);

    let userInfo;
    let userPosts;
    let postPagination;
    let userEvents;
    let eventPagination;
    let userDnft;
    let userBadges;
    if (res.status === 200 && res.data.success) {
      userInfo = res.data.data.user;
      userEvents = res.data.data.events;
      eventPagination = res.data.data.eventPagination;
      userPosts = res.data.data.posts;
      postPagination = res.data.data.postPagination;
      userDnft = res.data.data.dnft;
      userBadges = res.data.data.badges;
    } else {
      // API 호출에 실패하면 오류 메시지를 출력하고 빈 객체를 반환합니다.
      console.error('API 호출 실패:', res.data.message);
      userInfo = {};
      postPagination = {};
      userDnft = {};
      userBadges = {};
    }
    return {
      props: {
        userInfo,
        userEvents,
        eventPagination,
        userPosts,
        postPagination,
        userDnft,
        userBadges,
      },
    };
  } catch (error) {
    console.error('유저 정보를 가져오는데 실패했습니다:', error);

    return {
      props: {
        userInfo: null,
        postPagination: null,
        userDnft: null,
        userBadges: null,
      },
    };
  }
};
```
*마이페이지 SSR 코드*  
> 마이페이지 SSR 코드는 유저 페이지와 비슷하여 하나만 블로그에 작성했습니다.


### QR Code 스캔
{:toc}

![QR Code 스캔](../../assets/img/codestates/cleanmile/qr_code_scan.png)

*QR Code 스캔 페이지*  

관리자에서 발급한 QR 코드를 주최 측에서 이벤트 현장에 게시하면 이벤트에 참여한 유저가 QR 코드를 스캔 할 수 있다. QR 코드에는 해당 이벤트의 토큰이 담겨 있으며, 토큰을 서버에 전송하여 확인 후 유저에게 배지를 지급해 준다. 배지가 성공적으로 지급되면 마이페이지로 이동이 되며 배지를 확인할 수 있고, 배지가 지급이 되지 않으면 불가능하다는 Alert와 함께 마이페이지로 이동되도록 구현했다.

```tsx
import dynamic from 'next/dynamic';

// 동적 임포트를 사용하여 서버 사이드 렌더링(SSR) 없이 "react-web-qr-reader"를 가져옴
const QrReader = dynamic(() => import("react-web-qr-reader"), {
  ssr: false
});

const BADGE_TYPE = {
  1: 'bronze',
  2: 'silver',
  3: 'gold'
}

interface BadgeResponse {
  _id: string;
  badge_id: string;
  name: string;
  description: string;
  type: 1 | 2 | 3;
  image_url: string;
  token_uri: string;
  event_id: string;
  initial_quantity: number;
  remain_quantity: number;
  owners: [
    {
      _id: string;
    }
  ];
  created_at: string;
  updated_at: string;
}

const QRScan = () => {
  const router = useRouter();

  const [isScanned, setIsScanned] = useState(false);
  const [scanDelay, setScanDelay] = useState<number | false>(1000);

  /**
   * 이벤트 토큰 데이터를 기반으로 사용자 이벤트를 확인하는 함수
   * @param {string} tokenData - 이벤트 토큰 데이터
   */
  const verifyEvent = async (tokenData: string) => {
    Swal.fire({
      title: t('common:Loading'),
      allowOutsideClick: false,
      didOpen: () => {
        Swal.showLoading();
      }
    });

    try {
      const res = await userVerifyEvent(tokenData);
      
      Swal.close();
      setScanDelay(false);

      const userBadge: BadgeResponse = res.data.badge;

      if (res.status === 200) {
        setIsScanned(true);
        await Swal.fire({
          title: userBadge.name,
          html: `<p>${BADGE_TYPE[userBadge.type]}</p><br><p>${userBadge.description}</p>`,
          imageUrl: res.data.badge.image_url,
          imageWidth: 400,
          imageHeight: 200,
          imageAlt: 'Badge Image'
        });
        router.replace(`/users/mypage`);
      } else {
        dispatch(showErrorAlert(res.data.message));
        router.back();
      }
    } catch (error) {
      console.log(error)
      Swal.close();
      const err = error as AxiosError;

      const data = err.response?.data as { message: string };

      setIsScanned(true);
      setScanDelay(false); // 스캔 중지
      dispatch(showErrorAlert(data?.message));
    }
  }

  /**
   * QR 코드 스캔 결과를 처리하는 함수
   * @param {any} scanData - 스캔된 QR 데이터
   */
  const handleScan = (scanData: any) => {
    if (scanData && !isScanned) {
      setIsScanned(true); // 첫 번째 스캔 감지 시 isScanned 상태를 true로 설정
      setScanDelay(false); // 스캔을 일시 중지
      verifyEvent(scanData.data);
    }
  };

  /**
   * QR 코드 스캔 중 발생한 오류를 처리하는 함수
   * @param {any} err - 발생한 오류
   */
  const handleError = (err: any) => {
    console.error(err);
  };

  return (
    <div className="w-2/5 md:w-[70%] sm:w-[90%] xs:w-[90%] min-h-screen flex flex-col justify-center items-center gap-4 mx-auto">
      <div className='w-full flex justify-between items-center'>
        <div className='w-[10%] lg:w-[20%] sm:w-[20%] xs:w-[20%] flex items-center font-bold cursor-pointer hover:underline' onClick={() => router.push('/users/mypage')}>
          <IoIosArrowBack size={20} />
          {t('common:Back')}
        </div>
        <p className='w-[60%] lg:w-[75%] md:w-[70%] sm:w-[80%] xs:w-[80%] font-bold text-xl'>{t('common:Please scan the QR code')}</p>
      </div>
      { 
        !isScanned && 
        <QrReader
          facingMode='environment'
          delay={!scanDelay ? false : scanDelay}
          onError={handleError}
          onScan={handleScan}
          className="w-full" />
      }
    </div>
  );
};

export default QRScan;
```
*QR Code 스캔 코드*

### 헤더 상태 변경
{:toc}

![로그인하지 않은 경우의 헤더](../../assets/img/codestates/cleanmile/header.png)  
*로그인하지 않은 경우의 헤더*  
![로그인한 경우의 헤더](../../assets/img/codestates/cleanmile/header_login.png)
*로그인한 경우의 헤더*

로그인 하지 않은 상태에서는 로그인과 회원 가입 버튼이 보이며, 로그인한 경우에는 유저의 닉네임과 DNFT 이미지를 확인할 수 있다. 닉네임 옆의 토글 버튼을 클릭하면 글 작성 버튼, 마이페이지 이동 버튼, 로그아웃 버튼 등을 확인할 수 있다. 로그인 했을 때의 유저 정보는 `userInfo` API를 사용했고, `React Query`를 사용하여 유저 정보를 캐싱하여 `sessionStorage`에 저장해서 불러올 수 있도록 구현했다.  
유저가 로그아웃 버튼을 클릭하는 경우 `sessionStorage`와 `queryClient`에 저장한 정보를 모두 삭제하도록 구현했다.

```tsx
 /**
 * loginMutation 함수는 useMutation hook을 사용하여 loginAPI를 호출하고, 요청의 결과에 따라 적절한 동작을 수행
 * 
 * @returns {UseMutationResult} 리액트 쿼리의 useMutation hook으로부터 반환되는 결과 객체
 */
const loginMutation = useMutation(getUserInfo, {
 onSuccess: (data) => {
  queryClient.invalidateQueries('user_info');
  queryClient.setQueryData('user_info', data);

  const dehydratedState = dehydrate(queryClient);

  // Copying the dehydrated state
  let userInfoCache = { ...dehydratedState };

  // Keeping only 'user_info' cache
  userInfoCache.queries = dehydratedState.queries.filter((query) => query.queryKey === 'user_info');

  sessionStorage.setItem('user_info', JSON.stringify(userInfoCache));
  setUserData(data.data.data);
 },
 onError: (error) => {
  console.log('Mutation Error: ', error);
 }
});


useEffect(() => {
 if (isLoggedIn) {
  loginMutation.mutate();
 }
}, [isLoggedIn]);
```
*유저 정보 저장하는 코드*

```tsx
/**
 * 로그아웃 프로세스를 수행
 * 
 * @returns 로그아웃 처리 후 결과 데이터
 */
const performLogout = async () => {
 const res = await userLogout();

 if (res.status === 200) {
  dispatch(showSuccessAlert(res.data.message));
  router.push('/');
  setUserData(null);
  setIsLoggedIn(false);
  clearSession();
 } else {
  dispatch(showErrorAlert(res.data.message));
 }

 return res.data.data;
}

/**
 * 세션 정보 삭제
 */
const clearSession = () => {
 if (typeof window !== "undefined") {
  sessionStorage.removeItem('user');
  sessionStorage.removeItem('user_info');
 }
 queryClient.removeQueries('user');
 queryClient.removeQueries('user_info');
}

/**
 * 사용자가 로그아웃할 것인지 확인 후 로그아웃 처리 수행
 */
const logout = async () => {
 const result = await confirmLogout();

 if (result.isConfirmed) {
  try {
   await performLogout();
  } catch (error) {
   const err = error as AxiosError;
   const data = err.response?.data as { message: string };
   dispatch(showErrorAlert(data?.message));
  }
 } else if (result.isDismissed) {
  dispatch(showSuccessAlert(t('common:You have cancelled your logout')));
 }
}
```
*로그아웃 코드*

### 댓글 기능
{:toc}

![댓글 작성자가 아닌 경우](../../assets/img/codestates/cleanmile/comment.png)  
*댓글 작성자가 아닌 경우*  
![댓글 작성자인 경우](../../assets/img/codestates/cleanmile/comment_writer.png)
*댓글 작성자인 경우*

댓글의 경우 모든 게시글에 작성할 수 있다. 댓글은 로그인한 유저만 작성할 수 있고, 댓글 작성자인 경우 댓글 수정과 삭제가 가능하다. 댓글 작성자가 아닌 경우에는 좋아요만 클릭할 수 있다.

```tsx
/**
 * 댓글을 생성하는 함수
 */
const createComment = async () => {
 try {
  const res = await userCreateComment(postDetailId, comment);

  if (res.status === 200) {
   dispatch(showSuccessAlert(res.data.message));
   router.reload();
  } else {
   dispatch(showErrorAlert(res.data.message));
  }
 } catch (error) {
  const err = error as AxiosError;

  const data = err.response?.data as { message: string };

  dispatch(showErrorAlert(data?.message));
 }
}
```
*댓글 생성 코드*

```tsx
/**
 * 댓글에 '좋아요'를 표시하는 함수
 * @param {string} commentId - 좋아요를 누를 댓글의 ID
 */
const likeComment = async (commentId: string) => {
 try {
  const res = await userLikeComment(commentId);
  if (res.status === 200) {
   const updatedLikes = { ...likedComments, [commentId]: !likedComments[commentId] };
   setLikedComments(updatedLikes);

   localStorage.setItem('likedComments', JSON.stringify(updatedLikes));
  } else {
   dispatch(showErrorAlert(res.data.message));
  }

 } catch (error) {
  const err = error as AxiosError;

  const data = err.response?.data as { message: string };
  dispatch(showErrorAlert(data?.message));
 }
}

useEffect(() => {
 const storedLikes = localStorage.getItem('likedComments');
 if (storedLikes) {
  setLikedComments(JSON.parse(storedLikes));
 }
}, []);
```
*댓글 좋아요 기능 코드*

```tsx
/**
 * 댓글 편집 모드로 전환하는 함수
 * @param {string} commentId - 편집할 댓글의 ID
 */
const handleEditComment = (commentId: string) => {
 setEditingComment(commentId);
 setEditCommentInput(comment);
};

/**
 * 댓글을 편집하는 함수
 * @param {string} commentId - 편집할 댓글의 ID
 */
const editComment = async (commentId: string) => {

 try {
  const res = await userEditComment(commentId, editCommentInput);
  if (res.status === 200) {
   dispatch(showSuccessAlert(res.data.message));
   router.reload();
  } else {
   dispatch(showErrorAlert(res.data.message));
  }
 } catch (error) {
  const err = error as AxiosError;

  const data = err.response?.data as { message: string };

  dispatch(showErrorAlert(data?.message));
 }
}
```
*댓글 수정 코드*

```tsx
/**
 * 댓글을 삭제하는 함수
 * @param {string} commentId - 삭제할 댓글의 ID
 */
const deleteComment = async (commentId: string) => {
 const result = await confirmDelete();
 if (result.isConfirmed) {
  try {
   const res = await userDeleteComment(commentId);
   if (res.status === 200) {
    dispatch(showSuccessAlert(res.data.message));
    router.reload();
   } else {
    dispatch(showErrorAlert(res.data.message));
   }
  } catch (error) {
   const err = error as AxiosError;

   const data = err.response?.data as { message: string };

   dispatch(showErrorAlert(data?.message));
  }
 } else if (result.isDismissed) {
  dispatch(showSuccessAlert(t('common:You canceled deleting the comments')));
 }
}
```
*댓글 삭제 코드*

```tsx
<div className='flex justify-end items-center gap-4 sm:gap-2 xs:gap-2'>
 {likedComments[comment._id] ? (
  <AiFillHeart className='text-main-red cursor-pointer sm:w-[30%] xs:w-[30%]' size={26} onClick={() => likeComment(comment._id)} />
 ) : (
  <AiOutlineHeart className='text-main-red cursor-pointer sm:w-[30%] xs:w-[30%]' size={26} onClick={() => likeComment(comment._id)} />
 )}
 {/* ... comment content ... */}
 {isLoggedIn && userData?.user._id === comment.user_id?._id && (
  <>
   <MdOutlineCreate className="text-red-500 cursor-pointer sm:w-[30%] xs:w-[30%]" size={26} onClick={() => handleEditComment(comment._id)} />
   <AiOutlineDelete className="text-red-500 cursor-pointer sm:w-[30%] xs:w-[30%]" size={26} onClick={() => deleteComment(comment._id)} />
  </>
 )}
</div>
```
*로그인 및 댓글 작성자 여부에 따른 아이콘 표시 코드*

---

## 라이브러리 코드
{:toc}

### Redux
{:toc}

```bash
npm i redux
npm i redux-saga
npm i react-redux
npm i next-redux-wrapper
```

두 번째 프로젝트에서는 유저 정보를 `Redux`를 사용하여 관리를 했는데, `Redux` 스토어에 저장된 상태(state)는 페이지 새로고침 시 모든 상태가 초기화가 되어 적절하지 않은 사용법인 것 같았다. 그래서 이번에는 유저 정보가 아닌 Alert 상태를 `Redux`를 사용해 관리해 보았다. 그런데 Alert의 내용이 한 박자 늦게 뜨는 문제가 발생해, 왜 이런지 찾아보니 알고보니 `Redux`는 기본적으로 동기적인 액션만 지원하여, 비동기 작업을 수행하기 위해서는 추가적인 미들웨어를 사용해야 했던 것이다. 가장 널리 사용되는 두 가지 방법은 `Redux Thunk`와 `Redux Saga`가 있는데 조금 더 복잡한 비동기 작업을 처리할 수 있는 `Redux Saga`를 사용했다.  
아래는 해당 코드이다.  

```ts
export const SHOW_SUCCESS_ALERT = 'SHOW_SUCCESS_ALERT';
export const SHOW_ERROR_ALERT = 'SHOW_ERROR_ALERT';
export const CLOSE_ALERT = 'CLOSE_ALERT';

interface ShowSuccessAlertAction {
  type: typeof SHOW_SUCCESS_ALERT;
  payload: { message: string };
}

interface ShowErrorAlertAction {
  type: typeof SHOW_ERROR_ALERT;
  payload: { message: string };
}

interface CloseAlertAction {
  type: typeof CLOSE_ALERT;
}

export type AlertActionTypes =
  | ShowSuccessAlertAction
  | ShowErrorAlertAction
  | CloseAlertAction

export const showSuccessAlert = (message: string): AlertActionTypes => ({
  type: SHOW_SUCCESS_ALERT,
  payload: { message },
});

export const showErrorAlert = (message: string): AlertActionTypes => ({
  type: SHOW_ERROR_ALERT,
  payload: { message },
});

export const closeAlert = (): AlertActionTypes => ({
  type: CLOSE_ALERT,
});

```
*action.ts*
> alert 관련 기능을 관리하기 위한 액션 타입, 액션 생성자, 액션 인터페이스를 정의한 코드

- **액션 타입 정의**
  - `SHOW_SUCCESS_ALERT`, `SHOW_ERROR_ALERT`, `CLOSE_ALERT`는 `Redux` 액션의 유형을 나타내는 문자열 상수
  - 각 상수는 알림의 다른 동작(성공 알림 표시, 오류 알림 표시, 알림 닫기)를 나타냄
- **액션 인터페이스**
  - `ShowSuccessAlertAction`, `ShowErrorAlertAction`, `CloseAlertAction`는 각각의 액션 타입에 대한 `TypeScript` 인터페이스
  - `payload`는 액션에 관련된 추가 정보를 포함한다. 내 코드의 경우 메시지 문자열을 포함한다.
- `AlertActionTypes`는 위에서 정의한 모든 액션 인터페이스를 묶은 유니언 타입
- **액션 생성자 함수**
  - `showSuccessAlert`, `showErrorAlert`, `closeAlert` 액션 객체를 생성하는 함수들이다.
  - 이 함수들은 필요한 매개변수를 받아 액션 객체를 반환한다.

```ts
import { 
  AlertActionTypes, 
  CLOSE_ALERT, 
  SHOW_ERROR_ALERT, 
  SHOW_SUCCESS_ALERT, 
} from './actions';

export interface AlertState {
  type: 'success' | 'error' | null;
  message: string | null;
  isOpen: boolean;
}

const initialState: AlertState = {
  type: null,
  message: null,
  isOpen: false
};

export const alertReducer = (state = initialState, action: AlertActionTypes): AlertState => {
  switch (action.type) {
    case SHOW_SUCCESS_ALERT:
      return {
        type: 'success',
        message: action.payload.message,
        isOpen: true
      };
    case SHOW_ERROR_ALERT:
      return {
        type: 'error',
        message: action.payload.message,
        isOpen: true
      };
    case CLOSE_ALERT:
      return initialState;
    default:
      return state;
  }
};
```
*reducer.ts*
> `action.ts`에서 정의한 액션 타입과 액션 생성자에 대응하는 리듀서를 정의한 코드
> 리듀서는 액션에 따라 애플리케이션 상태를 변경하는 함수이다.

- **`State Interface`**
  - `AlertState` 인터페이스는 알림 상태의 형태를 정의한다.
    - `type` : 알림의 종류를 나타내며, `success`, `error` 또는 `null` 중 하나의 값을 가진다.
    - `message`: 표시할 알림 메시지, 없을 경우 `null`
    - `isOpen` : 알림이 현재 열려 있는지의 상태를 나타내는 `boolean` 값
- **`Initial State`**
  - 알림 상태의 초기 값을 정의
- **`Reducer`**
  - `alertReducer`는 알림 상태와 액션을 인자로 받아 새로운 상태를 반환하는 함수
  - `switch` 문을 사용하여 들어온 액션의 타입에 따라 상태를 업데이트한다.
    - `SHOW_SUCCESS_ALERT`: 성공 알림을 표시, 상태의 `type`을 `success`로, `message`를 액션에서 제공된 메시지로 설정하고, `isOpen`을 `true`로 설정
    - `SHOW_ERROR_ALERT`: 오류 알림을 표시, `type`이 `error`로 설정
    - `CLOSE_ALERT`: 알림을 닫음, 초기 상태(initialState)로 상태를 재설정
    - `default`: 알려지지 않은 액션 타입의 경우 현재 상태를 그대로 반환

```ts
import { combineReducers } from 'redux';
import { alertReducer } from './reducer';

const rootReducer = combineReducers({
  alert: alertReducer,
});

export default rootReducer;
```
*rootReducer.ts*
> `Redux`의 여러 리듀서를 하나로 합치기 위해 `combineReducers`를 사용하여 루트 리듀서를 생성하는 코드

- **`Root Reducer`**
  - `combineReducers` 함수는 객체를 인자로 받아 각 키에 대한 리듀서를 실행하고, 결과를 단일 상태 객체에 결합한다.
  - 여기서는 `alert`라는 키에 `alertReducer`를 연결하여 앱의 상태에서 `alert` 필드를 사용하여 알림 상태에 접근할 수 있다.
- 최종적으로 `rootReducer`를 내보내며, 이 루트 리듀서는 `Redux store`를 생성할 때 사용된다.


```ts
import { takeEvery, put, all, AllEffect, ForkEffect } from 'redux-saga/effects';
import Swal from 'sweetalert2';
import { 
  AlertActionTypes, 
  CLOSE_ALERT, 
  SHOW_ERROR_ALERT, 
  SHOW_SUCCESS_ALERT, 
  showSuccessAlert, 
  showErrorAlert
} from './actions';

/**
 * 주어진 액션으로부터 얻은 메시지를 토스트 알림으로 보여줌
 * 
 * @param {AlertActionTypes} action - 알림을 표시하기 위한 액션 타입
 */
function* showAlert(action: AlertActionTypes) {
  if ('payload' in action) {
    const { type, payload: { message } } = action;

    let icon: 'success' | 'error' = 'success';
    let title: string = 'Success';

    switch (type) {
      case SHOW_SUCCESS_ALERT:
        icon = 'success';
        break;
      case SHOW_ERROR_ALERT:
        icon = 'error';
        title = 'Error';
        break;
      default:
        break;
    }

    yield Swal.fire({
      title: title,
      text: message,
      icon: icon,
      toast: true, 
      position: 'top-end', 
      showConfirmButton: false,
      timer: 3000, 
      timerProgressBar: true,
      didOpen: (toast) => {
        toast.addEventListener('mouseenter', Swal.stopTimer)
        toast.addEventListener('mouseleave', Swal.resumeTimer)
      }
    });
  }

  // 알림이 표시된 후 상태에서 알림을 닫음
  yield put({ type: CLOSE_ALERT });
}

/**
 * 알림 관련 액션을 모니터링하고 해당 액션 발생 시 showAlert 함수를 실행
 */
function* watchAlerts(): Generator<AllEffect<ForkEffect<never>>, void, unknown> {
  yield all([
    takeEvery([
      SHOW_SUCCESS_ALERT, 
      SHOW_ERROR_ALERT, 
    ], showAlert)
  ]);
}

export default watchAlerts;
```
*sagas.ts*
> `Redux Saga`를 사용하여 알림 기능을 구현한 모듈
> `Redux Saga`는 `Redux` 애플리케이션의 사이드 이펙트 (예: 비동기 작업, 라우터 등)를 처리하기 위한 미들웨어이다.

- **`showAlert` 함수**
  - `showAlert`는 `AlertActionTypes` 액션을 인수로 받아 처리한다.
  - 액션에 `payload`가 포함되어 있으면, 알림 메시지를 포함하므로 그에 따른 처리를 수행한다.
  - 액션의 `type`에 따라 표시할 알림의 종류와 메시지를 결정한다.
  - `Swal.fire()` 함수를 사용하여 토스트 형태로 표시하도록 설정했다.
  - 알림 표시 후, `put` effect를 사용하여 `CLOSE_ALERT` 액션을 디스패치하여 상태에서 알림을 닫는다.
- **`watchAlerts`**
  - 알림 관련 액션을 모니터링하여 해당 액션들이 디스패치될 때마다 `showAlert` 함수를 호출한다.
  - `takeEvery`는 지정된 액션들이 디스패치될 때마다 지정된 `saga` 함수(`showAlert`)를 호출하는 데 사용된다.
  - `all`은 여러 사가 이펙트를 동시에 수행할 수 있게 해준다.
- `watchAlerts` 
  - saga를 기본으로 내보낸다.
  - 애플리케이션의 루트 saga에서 사용되거나 미들웨어에 연결될 수 있다.

```tsx
const dispatch = useDispatch();

const editPost = async () => {
 try {
  const updatedPostId = await updatePost(reviewDetailDefault._id, title, content, images, videos);
  dispatch(showSuccessAlert(t('Success')));
  router.replace(`/posts/review/${updatedPostId}`);
 } catch (error) {
  const err = error as AxiosError;

  const data = err.response?.data as { message: string };

  dispatch(showErrorAlert(data?.message));
 }
}
```
*`dispatch` 사용 예시*

### React Query
{:toc}

```bash
npm i react-query
```

이번 프로젝트에서는 `React Query`를 사용하여 유저 정보를 캐싱하여 저장하 수 있도록 구현을 해보았다. `React Query`는 `React` 애플리케이션에서 서버 상태를 동기화하고 캐싱하는 데 도움을 주는 라이브러리이다. `React Query`는 한 번 서버에서 데이터를 가져오면 메모리에 캐싱한다. 이후 동일한 데이터를 요청하면 서버에 다시 요청하는 대신 캐시에서 바로 데이터를 가져올 수 있어, 사용자에게 더 빠른 응답 시간을 제공하며, 서버 부하도 줄일 수 있다. 또한 설정에 따라 데이터를 주기적으로 다시 가져오거나 특정 상호작용 후 데이터를 다시 가져올 수 있다. 이를 통해 애플리케이션의 데이터가 항상 최신 상태로 유지되게 할 수 있다는 장점들이 있다.
아래는 내가 `React Query`를 사용한 코드 중 하나이다.

```tsx

  /**
   * loginMutation 함수는 useMutation hook을 사용하여 loginAPI를 호출하고, 요청의 결과에 따라 적절한 동작을 수행
   * 
   * @returns {UseMutationResult} 리액트 쿼리의 useMutation hook으로부터 반환되는 결과 객체
   */
  const loginMutation = useMutation(getUserInfo, {
    onSuccess: (data) => {
      queryClient.invalidateQueries('user_info');
      queryClient.setQueryData('user_info', data);

      const dehydratedState = dehydrate(queryClient);

      // Copying the dehydrated state
      let userInfoCache = { ...dehydratedState };

      // Keeping only 'user_info' cache
      userInfoCache.queries = dehydratedState.queries.filter((query) => query.queryKey === 'user_info');

      sessionStorage.setItem('user_info', JSON.stringify(userInfoCache));
      setUserData(data.data.data);
    },
    onError: (error) => {
      console.log('Mutation Error: ', error);
    }
  });


  useEffect(() => {
    if (isLoggedIn) {
      loginMutation.mutate();
    }
  }, [isLoggedIn]);


  /**
   * 로그아웃할 것인지 확인하는 다이얼로그를 표시
   * 
   * @returns Swal의 Promise 결과 객체
   */
  const confirmLogout = () => {
    return Swal.fire({
      title: t('common:Do you want to log out'),
      icon: 'question',
      showCancelButton: true,
      confirmButtonText: t('common:OK'),
      confirmButtonColor: '#6BCB77',
      cancelButtonText: t('common:Cancel'),
      cancelButtonColor: '#FF6B6B'
    });
  }

  /**
   * 로그아웃 프로세스를 수행
   * 
   * @returns 로그아웃 처리 후 결과 데이터
   */
  const performLogout = async () => {
    const res = await userLogout();

    if (res.status === 200) {
      dispatch(showSuccessAlert(res.data.message));
      router.push('/');
      setUserData(null);
      setIsLoggedIn(false);
      clearSession();
    } else {
      dispatch(showErrorAlert(res.data.message));
    }

    return res.data.data;
  }
```
- **데이터 동기화 및 캐싱**
  - `useMutation`을 사용하여 `getUserInfo` API를 호출하며, 요청이 성공하면 캐시를 업데이트한다. `queryClient.invalidateQueries('user_info')`는 해당 쿼리의 데이터가 더 이상 유효하지 않다고 표시하여 새로운 데이터로 동기화하게 만든다.
  - `queryClient.setQueryData('user_info', data)`를 통해 직접 user_info 쿼리의 캐시 데이터를 설정한다.
- **데이터 저장 및 복원**
  - `sessionStorage`를 사용하여 `user_info`의 캐시 정보를 세션 저장소에 저장한다. 이를 통해 페이지를 새로고침하거나 탭을 닫았다가 다시 열었을 때 이전의 캐시 데이터를 빠르게 가져올 수 있다.
- **에러 핸들링**
  - `onError` 옵션을 사용하여 API 요청이 실패했을 때의 에러를 처리한다.
- **요청 최적화**
  - `useEffect` 내에서 `isLoggedIn` 상태가 변경될 때만 `loginMutation.mutate()`를 호출하여 불필요한 재요청을 최소화한다.

이번에 `React Query`를 처음 사용해서 많이 헤맸고, `userInfo` API에서만 사용했지만 다음에는 다른 API에도 적용해 볼 생각이다.


### 다국어 기능
{:toc}

```bash
npm i --save next-translate
npm i next-translate-plugin
```


![다국어 기능](../../assets/img/codestates/cleanmile/header.png)  
![다국어 기능](../../assets/img/codestates/cleanmile/header_i18n.png)  
*다국어 기능*  

이번 프로젝트에서 어쩌다 보니 전부 영어로 표기하게 되긴 했는데 다국어 기능을 할 생각은 없었다. 그런데 멘토분과 면담 중 '왜 다들 영어로만 사이트를 만드느냐'라는 소리를 듣고 생각해보니 맞는 말이었다. 나도 영어로만 된 사이트에 접속했을 때 불편함이 많았으면서 나도 영어로 사이트를 제작하고 있었던 것이었다. 그래서 주요 기능들을 어서 끝내고 다국어 기능을 만들어야겠다 싶었다.  
라이브러리를 찾던 중 `Next Translate`라는 것을 발견했는데, 사용법이 간단해 보여 해당 라이브러리를 사용하기로 결정했다.
헤더에서 `EN`과 `KO`라는 버튼이 있는데 기본으로 `EN`이 선택되어 있으며, `KO` 버튼을 클릭하면 한국어로 변경이 되도록 구현했다.  

```js
const path = require('path');
const nextTranslate = require('next-translate-plugin');

/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: false,
  images: {
    domains: [
      'd190dv1poq5i84.cloudfront.net',
      'clean-mile.s3.ap-northeast-2.amazonaws.com',
      'plohub-bucket.s3.ap-northeast-2.amazonaws.com',
      'gold-cool-goat-213.mypinata.cloud',
    ],
  },
  remotePatterns: [
    {
      protocol: 'https',
      hostname: 'd190dv1poq5i84.cloudfront.net',
      port: '',
    },
  ],
  webpack: (config, { dev }) => {
    if (dev) {
      // Only dev purpose
      config.devtool = 'cheap-module-source-map';
    }
    // Alias 설정 추가
    config.resolve.alias['@next-translate-root/locales'] = path.resolve(__dirname, 'locales');
    return config;
  },
  output: 'standalone',
};

module.exports = nextTranslate(nextConfig);
```
*next.config.js*

```json
{
  "locales": ["en", "ko"],
  "defaultLocale": "en",
  "localeDetection": false,
  "pages": {
    "*": ["common"]
  }
}
```
*프로젝트 최상위 루트, i18n.json*

프로젝트에서 `en(English)`, `ko(Korean)`을 지원하며, 기본 언어는 `en`이다.  
모든 페이지는 `common`이라는 네임스페이스의 번역을 사용할 것이라는 것을 정의한다.

```json
{
  "Get Started": "Get Started",
  "Info" : "Info",
  "Notice" : "Notice",
  "Events" : "Events",
  "Event" : "Event",
  "Community" : "Community",
  "Login" : "Login",
  "Register" : "Register",
  "General" : "General",
  "Review" : "Review",
  "Write" : "Write",
  "Profile" : "Profile",
  "Logout" : "Logout",
  "No" : "No.",
  "Title" : "Title",
  "Content" : "Content",
  "Writer" : "Writer",
  "Date" : "Date",
  "Views" : "Views",
  "Search" : "Search",
  "Latest order" : "Latest order",
  "Old order" : "Old order",
  "View order" : "View order",
  "Comment" : "Comment",
  "List" : "List",
  "Read more" : "Read more",
  "All": "All",
  "Before proceeding": "Before proceeding",
  "Recruiting": "Recruiting",
  "End of recruitment": "End of recruitment",
  "In progress": "In progress",
  "End of progress": "End of progress",
  "Cancel Progress": "Cancel Progress",
  "Unknown": "Unknown",
  "E-Mail": "E-Mail",
  "Nickname": "Nickname",
  "Name": "Name",
  "Phone Number": "Phone Number",
  "Password": "Password",
  "Password Confirm": "Password Confirm",
  "Confirm": "Confirm",
  "MetaMask Connect": "MetaMask Connect",
  "SignUp": "SignUp",
  "KaKao": "KaKao",
  "Google": "Google",
  "There are no registered posts": "There are no registered posts.",
  "You have cancelled deleting the post": "You have cancelled deleting the post.",
  "No post was created": "No post was created",
  "No events participated": "No events participated",
  "There are no registered badges": "There are no registered badges",
  "Posts created": "Posts created",
  "Profile change was successful": "Profile change was successful",
  "Your wallet address has been copied": "Your wallet address has been copied",
  "Failed to copy wallet address": "Failed to copy wallet address",
  "Participated Events": "Participated Events",
  "First come, first served": "First come, first served",
  "User does not exist": "User does not exist.",
  "Draw lots": "Draw lots",
  "Event Type": "Event Type",
  "Status": "Status",
  "Save": "Save",
  "Edit": "Edit",
  "Delete": "Delete",
  "Create": "Create",
  "Create Posts": "Create Posts",
  "Please select a category": "Please select a category.",
  "Please enter the title": "Please enter the title.",
  "Please select a file": "Please select a file.",
  "Select File": "Select File",
  "Please enter comments": "Please enter comments.",
  "Edit General Posts": "Edit General Posts",
  "Edit Review Posts": "Edit Review Posts",
  "Please enter the number without '-'": "Please enter the number without '-'.",
  "Password must be at least 8 characters long": "Password must be at least 8 characters long.",
  "Password must contain all English uppercase letters, lowercase letters, numbers, and special symbols": "Password must contain all English uppercase letters, lowercase letters, numbers, and special symbols.",
  "Invalid email format": "Invalid email format.",
  "Nickname must be at least 2 characters long": "Nickname must be at least 2 characters long.",
  "Nickname can be up to 8 characters": "Nickname can be up to 8 characters.",
  "Password matches": "Password matches.",
  "Password doesn't match": "Password doesn't match.",
  "Your email verification code has been sent": "Your email verification code has been sent.",
  "Enter your verification code": "Enter your verification code.",
  "Enter your code here": "Enter your code here.",
  "Your email has been successfully authenticated": "Your email has been successfully authenticated..",
  "MetaMask Address": "MetaMask Address",
  "Instagram Connect": "Instagram Connect",
  "DNFT Upgrade": "DNFT Upgrade",
  "Are you sure you want to delete it": "Are you sure you want to delete it?",
  "Completed application": "Completed application",
  "Do you want to log out": "Do you want to log out?",
  "You have cancelled your logout": "You have cancelled your logout.",
  "You canceled deleting the comments": "You canceled deleting the comments.",
  "Password requirements not met": "Password requirements not met.",
  "Verify": "Verify",
  "Token Exchange": "Mileage Exchange",
  "Mileage": "Mileage",
  "Token": "Token",
  "Total Badge Score": "Total Badge Score",
  "OK": "OK",
  "Entry": "Entry",
  "Success": "Success!",
  "Error": "Error",
  "Cancel": "Cancel",
  "Back": "Back",
  "Please scan the QR code": "Please scan the QR code.",
  "Upgrading": "Upgrading...",
  "Loading": "Loading...",
  "QR Code Scan": "QR Code Scan",
  "Warning": "Warning!",
  "You need to log in": "You need to log in.",
  "It is a community service that aims to collect information about environmental protection events in one place to improve accessibility and user-friendliness, and to encourage active participation by issuing certification badges (NFTs) to users who participate in events": "It is a community service that aims to collect information about environmental protection events in one place to improve accessibility and user-friendliness, and to encourage active participation by issuing certification badges (NFTs) to users who participate in events.",
  "The project was born out of the idea to facilitate interaction between people interested in protecting the environment, and to encourage participants to contribute to solving and improving environmental problems such as urban aesthetics, impaired drainage, loss of biodiversity, air pollution, and resource depletion": "The project was born out of the idea to facilitate interaction between people interested in protecting the environment, and to encourage participants to contribute to solving and improving environmental problems such as urban aesthetics, impaired drainage, loss of biodiversity, air pollution, and resource depletion."
}
```
*최상위 루트, locales/en/common.json*

```json
{
  "Get Started": "시작하기",
  "Info": "정보",
  "Notice": "공지사항",
  "Events": "이벤트",
  "Event": "이벤트",
  "Community": "커뮤니티",
  "Login": "로그인",
  "Register": "회원가입",
  "General": "자유 게시판",
  "Review": "리뷰 게시판",
  "Write": "글쓰기",
  "Profile": "프로필",
  "Logout": "로그아웃",
  "No": "번호",
  "Title": "제목",
  "Content": "내용",
  "Writer": "작성자",
  "Date": "날짜",
  "Views": "조회수",
  "Search": "검색",
  "Latest order": "최신 순",
  "Old order": "오래된 순",
  "View order": "조회수 순",
  "Comment": "댓글",
  "List": "목록",
  "Read more": "더 보기",
  "All": "전체",
  "Before proceeding": "모집 전",
  "Recruiting": "모집 중",
  "End of recruitment": "모집 종료",
  "In progress": "진행 중",
  "End of progress": "진행 종료",
  "Cancel Progress": "진행 취소",
  "Unknown": "알수없음",
  "E-Mail": "이메일",
  "Nickname": "닉네임",
  "Name": "이름",
  "Phone Number": "핸드폰번호",
  "Password": "비밀번호",
  "Password Confirm": "비밀번호 확인",
  "MetaMask Connect": "메타마스크 연결",
  "Confirm": "확인",
  "SignUp": "회원가입",
  "KaKao": "카카오톡",
  "Google": "구글",
  "There are no registered posts": "등록된 게시글이 없습니다.",
  "You have cancelled deleting the post": "게시글 삭제를 취소하셨습니다.",
  "No post was created": "작성한 게시글이 없습니다.",
  "No events participated": "참여한 이벤트가 없습니다.",
  "There are no registered badges": "등록된 배지가 없습니다.",
  "Posts created": "작성한 게시글",
  "Profile change was successful": "프로필 변경되었습니다.",
  "Your wallet address has been copied": "지갑주소가 복사 되었습니다.",
  "Failed to copy wallet address": "지갑주소 복사에 실패했습니다.",
  "Participated Events": "참여한 이벤트",
  "First come, first served": "선착순",
  "User does not exist": "존재하지 않는 사용자입니다.",
  "Draw lots": "추첨제",
  "Event Type": "모집 방법",
  "Status": "상태",
  "Save": "저장",
  "Edit": "수정",
  "Delete": "삭제",
  "Create Posts": "게시글 작성",
  "Please select a category": "카테고리를 선택해 주세요.",
  "Please enter the title": "제목을 입력해 주세요.",
  "Please select a file": "파일을 선택해 주세요.",
  "Select File": "파일 선택",
  "Please enter comments": "댓글을 입력하세요.",
  "Edit General Posts": "자유 게시글 수정",
  "Edit Review Posts": "리뷰 게시글 수정",
  "Please enter the number without '-'": "'-'없이 번호만 입력해주세요.",
  "Password must be at least 8 characters long": "비밀번호는 최소 8자 이상이어야 합니다.",
  "Password must contain all English uppercase letters, lowercase letters, numbers, and special symbols": "비밀번호는 영문 대문자, 영문 소문자, 숫자, 특수기호를 모두 포함해야 합니다.",
  "Invalid email format": "이메일 형식에 맞지 않습니다.",
  "Nickname must be at least 2 characters long": "닉네임은 최소 2자 이상이어야 합니다.",
  "Nickname can be up to 8 characters": "닉네임은 최대 8자 입니다.",
  "Password matches": "비밀번호가 일치합니다.",
  "Password doesn't match": "비밀번호가 일치하지 않습니다.",
  "Your email verification code has been sent": "이메일 인증 코드가 발송되었습니다.",
  "Enter your verification code": "인증 코드를 입력해주세요.",
  "Enter your code here": "코드를 입력해주세요.",
  "Your email has been successfully authenticated": "이메일 인증되었습니다.",
  "MetaMask Address": "지갑 주소",
  "Instagram Connect": "인스타그램 연결",
  "DNFT Upgrade": "DNFT 업그레이드",
  "Are you sure you want to delete it": "삭제하시겠습니까?",
  "Completed application": "신청 완료",
  "Do you want to log out": "로그아웃 하시겠습니까?",
  "You have cancelled your logout": "로그아웃이 취소되었습니다.",
  "You canceled deleting the comments": "댓글 삭제가 취소되었습니다.",
  "Password requirements not met": "비밀번호 형식에 맞지 않습니다.",
  "Verify": "인증",
  "Token Exchange": "토큰 교환",
  "Mileage": "마일리지",
  "Token": "토큰",
  "Total Badge Score": "총 배지 점수",
  "Create": "생성",
  "OK": "확인",
  "Entry": "신청",
  "Success": "성공",
  "Error": "오류",
  "Cancel": "취소",
  "Back": "뒤로가기",
  "Please scan the QR code": "QR 코드를 스캔해주세요.",
  "Upgrading": "업그레이드 중...",
  "Loading": "로딩 중...",
  "QR Code Scan": "QR 코드 스캔",
  "Warning": "주의!",
  "You need to log in": "로그인이 필요합니다.",
  "It is a community service that aims to collect information about environmental protection events in one place to improve accessibility and user-friendliness, and to encourage active participation by issuing certification badges (NFTs) to users who participate in events": "환경 보호 행사에 대한 정보를 한 곳에 모아서 접근성과 사용자 편의성을 증진시키고, 행사에 참여하는 사용자들에게 인증 배지(NFT)를 발급하여 활발한 참여를 유도하는 것을 목표로 하는 커뮤니티 서비스입니다.",
  "The project was born out of the idea to facilitate interaction between people interested in protecting the environment, and to encourage participants to contribute to solving and improving environmental problems such as urban aesthetics, impaired drainage, loss of biodiversity, air pollution, and resource depletion": "이 프로젝트는 환경 보호에 관심이 있는 사람들 간의 상호작용을 촉진하고, 참여자들이 자발적으로 참여하도록 유도하여 도시 미관 훼손, 배수 시설 훼손, 생물 다양성 훼손, 대기 오염, 자원 고갈 등의 환경 문제를 해결하고 개선하는 데 기여하고자 하는 아이디어에서 시작하였습니다."
}
```
*최상위 루트, locales/ko/common.json*

위와 같이 번역할 내용을 `json`에 하드코딩하여 작성한다.

아래는 프로젝트에 적용한 코드이다.

```tsx
import useTranslation from 'next-translate/useTranslation';

const Header = () => {
  const { t } = useTranslation('common');


  return (
    <>
      <div className="w-full mx-auto h-20 flex items-center justify-between px-10 sm:px-3 xs:px-3 border-b bg-white md:gap-6 sm:gap-4 xs:gap-4 sticky top-0 z-50">
        <div className="w-3/4 md:w-full sm:w-full h-full flex justify-end items-center gap-10">
          <nav className='flex justify-center items-center md:hidden sm:hidden xs:hidden relative'>
            <ul className="flex justify-center items-center gap-14">
              <li className={
                `flex 
                justify-center 
                items-center 
                font-semibold 
                cursor-pointer 
                hover:text-green-600 
                transition 
                duration-200 
                ${router.pathname === '/' ? 'text-green-600' : null}`}
              >
                <Link href='/'>
                  {t('common:Info')}
                </Link>
              </li>
              <li className={
                `flex 
                justify-center 
                items-center 
                font-semibold 
                cursor-pointer 
                hover:text-green-600 
                transition 
                duration-200 
                ${router.pathname === '/notice' ? 'text-green-600' : null}`}
              >
                <Link href='/notice'>
                  {t('common:Notice')}
                </Link>
              </li>
              <li className={
                `flex 
                justify-center 
                items-center 
                font-semibold 
                cursor-pointer 
                hover:text-green-600 
                transition 
                duration-200 
                ${router.pathname === '/posts/events' ? 'text-green-600' : null}`}
              >
                <Link href='/posts/events'>
                  {t('common:Events')}
                </Link>
              </li>
              <li className={
                `flex 
                justify-center 
                items-center 
                font-semibold 
                cursor-pointer 
                hover:text-green-600 
                transition 
                duration-200 
                ${router.pathname === '/posts/general' || router.pathname === '/posts/review' ? 'text-green-600' : null}`}
                onClick={() => setIsMenu(!isMenu)}>
                {t('common:Community')}
              </li>
              {isMenu && (
                <ul className="w-[30%] bg-white flex flex-col justify-center items-center border rounded-xl absolute z-50"
                  style={{ top: '150%', right: 80 }}>
                  <li className='w-full text-center list-none cursor-pointer px-5 py-3 font-semibold hover:bg-green-600 hover:text-white hover:rounded-xl'>
                    <Link href='/posts/general'>
                      {t('common:General')}
                    </Link>
                  </li>
                  <li className='w-full text-center list-none cursor-pointer px-5 py-3 font-semibold hover:bg-green-600 hover:text-white hover:rounded-xl'>
                    <Link href='/posts/review'>
                      {t('common:Review')}
                    </Link>
                  </li>
                </ul>
              )}
              <LanguageSwitch />
            </ul>
          </nav>
        </div>
      </div>
    </>
  );
};

export default Header;
```

`next-translate`에서 제공하는 `useTranslation`훅의 `t`함수를 사용하면 다국어를 지원할 수 있다. `t` 함수를 사용할 때에는 어떤 언어 파일(`common`)의 어떤 단어(`Review`)를 사용할지 전달해야 한다.


## 마무리
{:toc}

드디어 마지막 프로젝트가 끝났다. 이번에는 마지막 프로젝트인 만큼 기획도 오래 걸렸고 오래 걸린 만큼 할 일도 많았다. 게다가 새로운 기술들을 시도해서 더욱 어려웠던 것 같다. 특히 이번에는 타입스크립트를 사용해봤는데, 옛날에 강의 들었다가 안들은지 오래돼서 다 까먹은 상태로 진행을 해 솔직히 GPT한테 부탁한 게 태반이다. 그래도 후반에 되서야 조금 감을 잡았는데, 함수들 쪽에서 타입을 지정하는 부분이 아직은 좀 어려운 것 같다. 게다가 빌드 하는 과정에서 타입을 지정하지 않으면 오류가 난다는 것도 처음 알았다. 솔직히 좀 귀찮고 작업 속도가 오래 걸리기도 해서 아직은 크게 장점을 잘 모르겠다. 그래도 자바스크립트 메소드를 사용하는 부분이나 서버로 데이터를 전송하는 부분에서 타입을 확실하게 지정하니 좀 편한 부분도 있는 것 같다. 다른 여러 장점들은 타입스크립트를 계속해서 써봐야 체감이 될 것 같다.  
그리고 리덕스를 쓰는 과정에서 리덕스가 동기적으로 작업한다는 것을 사실 이번에 처음 알았다. 이전에는 그저 '상태 관리 라이브러리, 전역적으로 상태를 관리할 수 있음' 정도로만 썼는데 미들웨어를 사용해서 비동기적으로 처리하는 등 이번에야 제대로 조금 사용한 것 같다. 리덕스 역시 앞으로 공부할 부분이 많고 계속해서 써야 어떤식으로 동작이 되는지 확실히 이해할 수 있을 것 같다. 지금은 그저 GPT한테 물어보면서 사용해서 제대로 알고 사용했다고 할 수 없는 상태이다. 프로젝트를 끝내기 급급한데다가 프로젝트 시간도 짧다 보니 파악할 시간이 부족했다. 리액트 쿼리 또한 동일하다. 특히 `userInfo` API를 연결하는 부분에서 `session`에 데이터를 저장 후 가져오다 보니 헤더에서 유저 정보가 새로고침을 해야 불러오는 상황이 발생했는데, 일단은 `useState`를 사용하여 데이터를 직접 저장 후 불러오는 형식을 사용했다. 이렇게 하니 새로고침을 하지 않더라도 로그인 후 메인페이지로 이동하면 `userInfo`의 데이터를 바로 받아오는 것을 확인할 수 있었다. 이런 처리 방법이 맞는 것인지, 아닌지는 좀 더 찾아봐야 알 수 있을 것 같다.  
이번에는 너무 많은 새로운 기술을 사용하려다 보니 기술들을 이해하는 데에는 부족한 점이 많았다. 너무 욕심을 부린 것 같은데, 그 만큼 해보고 싶고 하고 싶은 것이 많았다. 프론트엔드에서 필수라고 여겨질 만큼 많은 회사에서 사용하는 것 같아 시도를 해봤는데 역시 아직 갈 길이 멀었다는 생각이 든다. 그래도 많이 사용하는 만큼 장점이 많다는 뜻이니 틈틈히 공부해서 다음에는 GPT의 도움 없이 사용할 수 있게 되고 싶다.

마무리는 두서 없이 생각나는 대로 쓰다 보니 말이 이리저리 안맞고 왔다 갔다 할 수도 있지만, 이번 프로젝트에 대한 솔직한 생각이다.

---
> [Git Hub Repository](https://github.com/codestates-beb/beb-09-clean-mile)  
> [Team Notion](https://codestates.notion.site/4-6ec71403fea14dac8864eebae1c38370)  
> <a href='/assets/download/Clean-mile.pdf' download>발표 PPT 파일</a>
