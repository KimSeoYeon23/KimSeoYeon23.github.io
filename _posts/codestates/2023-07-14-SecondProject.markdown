---
layout: post
title:  "CodeStates BEB 두 번째 프로젝트 회고"
date:   2023-07-14 09:30:00 +0900
categories: 
  - Dev
  - codestates
tag: codestates
comments: true
---

![Community](../../assets/img/codestates/plohub/community.jpeg){:.centered}

## 프로젝트 기간 : 2023.07.03 ~ 2023.07.14

## 개요  
**인센티브 기반 커뮤니티란?**  

인센티브 기반 커뮤니티란, 어떠한 SNS 활동을 하면 서버에서 인센티브를 지급하는 서비스를 말한다.  
예를 들면, [스팀잇(steemit)](https://steemit.com/)이라는 커뮤니티가 있다. 스팀잇은 블록체인 기반의 SNS 중 많은 사람이 사용하고 있는 프로젝트이며, 콘텐츠는 모두 text로 변환되어 블록체인에 저장되고, upvote와 downvote시에 steempower에 따른 보상이 작가와 큐레이터에게 주어진다.

우리 팀은 플로깅(Plogging)을 주제로 블록체인 인센티브 기반 커뮤니티를 구현했다.
- **플로깅이란?**  
    플로깅이란 조깅과 쓰레기 줍기의 조합으로, 스웨덴어 동사 plocka upp와 jogga를 결합한 단어 이다.  
    쉽게 말해 쓰래기 줍기와 조깅을 결합한 활동으로 조깅을 하며 동시에 산책로나 길가에 버려져 있는 쓰래기를 줍는 행위 이다.  
- **주제 선정 이유**  
    최근 SNS나 인터넷을 통해 개인의 건강관리 활동이나 환경보존이라는 키워드는 모두가 쉽게 접하고 현재 사람들의 관심도가 매우 높은 키워드들 이다.  
    따라서 저희는 이 두가지 키워드를 합한 플로깅이란 활동이 트랜디하게 느껴졌고 아직 우리나라에는 플로깅과 관련된 플랫폼이 전무한 상태이기 때문에 플로깅에 대한 정보 공유, 후기등을 작성하고 이런 커뮤니티 활동을 통해 얻은 보상으로 NFT를 민팅, ETH와 교환, 유저 간 토큰 거래가 가능한 커뮤니티를 만들기로 했다.

****

## 포지션
이번 두 번째 프로젝트에서는 불가피하게 팀 인원이 3명이 배정됐다. 다른 팀원 분들은 모두 백엔드라 프론트엔드는 나 혼자 맡게 됐는데, 막막함과 동시에 오히려 나쁘지 않다고 생각했다. 이 기회에 내가 해보고 싶었던 것들을 해볼 수 있는 기회라고 생각했기 때문이다. 첫 프로젝트에서는 팀장도 맡게 되어 스트레스도 받고 신경써야 할 일이 너무 많아서 힘들었는데, 이번 프로젝트에서는 다행히 팀장은 안 맡게 되어 온전히 내 일에 집중할 수 있었다. 이번에 팀장을 맡아주신 팀원 분이 너무 잘해주셔서 그런 것도 있었던 것 같다. Docker를 꼭 써보고 싶었는데 마침 Docker 설정까지 해주시고, git 브랜치, 커밋 규칙까지 모두 정하니 첫 프로젝트에 비해 체계를 확실히 잡고 진행하니 꽤나 순조롭게 프로젝트를 진행 할 수 있었다.

***

## 팀 규칙  
### 그라운드 룰  
1. 10시 스탠드 업 미팅 (전날 작성한 코드 설명, 오늘 목표)
2. 5시 진행도 공유
3.  바른 말 고운 말 사용하기
4. 개인사정이 생길 경우, 팀원들에게 미리(오전 중으로) 알리기
5. 질문이 있는 경우, 줌에서 바로 호출
6. 오류 발생 시, 오류 제보 채널에 오류 로그를 복사 붙여넣기 또는 화면 캡쳐하여 올리고 줌으로 호출

### 깃허브 브랜치 관리 규칙  
1. main, dev 브랜치는 팀장이 직접 관리 (팀장 허가 필요)
2. 브랜치 이름은 새로운 기능을 추가할 때마다 'git checkout -b feature/기능이름'으로 생성하여 해당 브랜치에서 작업
3. pull request를 작성하면 줌으로 팀장 호출
4. 브랜치 merge가 완료되면 팀장은 팀원들에게 공지

### 커밋 메시지 규칙
```
Fix: 올바르지 않은 동작을 고친 경우  
Add: 파일 또는 새로운 기능 추가가 있을 때  
Remove: 코드나 파일의 삭제가 있을 때  
Update: 기존의 코드를 수정, 추가, 보완  
Refactor: 전면 수정
```
> git commit -m "Add 영어로 제목 적기"

### 커밋 순서
```
1. git add .
2. git commit "커밋 메시지"
3. git fetch origin dev
4. git rebase origin/dev
5. git push origin 작업중인 브랜치
6. 브랜치에서 작업을 마친 경우, pull request 생성
```

### .gitignore 기본 설정
```
1. node_modules
2. .env
3. package-lock.json
```
> .env를 ignore하는 대신 .env.example로 어떤 값이 필요한지 명시

### node, npm 버전 정보
```
1. node - 16.14.0
2. npm - 9.6.4
```

### Linter
```
- VSCode Prettier extension 사용
- 1 tab = 공백 4칸
```

***

## 구현 목표
**Bare Minimum**  
- 로그인 로직
  - 회원가입
  - 로그인
  - 로그아웃
- 회원 등급 나누기 (토큰 수량에 따라)
  - 글 작성 제한
- NFT 민팅
    - 이미지는 자유롭게 업로드
        - 쓰레기 정리한 사진(권고 사항)
- 게시글 작성 (회원 등급 별로)
  - lv1. : 플로깅 참여 후기, 행사 정보 올리기 작성 가능
  - lv2. : 플로깅 참여 후기, 행사 정보, 코스 정보 작성 가능
- 마이페이지
  - 닉네임 설정 가능
      - default : 회원가입 시 발행한 지갑주소
  - 보유한 NFT 개수 확인
  - 보유한 토큰 수량 확인
  - 작성한 게시글 리스트
  - 토큰 -> ETH 스왑 기능
  - 토큰 전송 기능
  - 본인의 레벨
- 게시글 상세 페이지
  - 게시글 삭제 기능
  - 댓글 기능
    - 댓글 작성
    - 댓글 삭제

**Advanced**  
- 게시물 NFT로 만들기 기능
    - NFT로 만들지 유저 선택(체크박스)
    - NFT로 발행한 게시글은 수정, 삭제 불가
- 게시물 검색
- 게시물 수정
- NFT 판매

**Nightmare**
- Admin 페이지

프론트엔드의 목표는 이렇다. Bare Minimum을 최소 목표로 잡고, 해당 기능들을 모두 구현하고 시간이 남을 경우 Advanced, Nightmare를 구현하기로 정했다.

## 프로젝트 기획
![서비스아키텍쳐](../../assets/img/codestates/plohub/service_archtecture.png){:.centered}
*와이어 프레임*  

![FlowChart](../../assets/img/codestates/plohub/flow_chart.png){:.centered}
*플로우 차트*  

![와이어프레임](../../assets/img/codestates/plohub/wireframe.png){:.centered}
*와이어 프레임*  

## 기술 스택
**Front-end**  
<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26.svg?style=for-the-badge&logo=HTML5&logoColor=white"/>
<img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=CSS3&logoColor=white"/>
<img alt="Javascript" src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=for-the-badge&logo=JavaScript&logoColor=white"/>
<img alt="Next.js" src="https://img.shields.io/badge/Next.js-000000.svg?style=for-the-badge&logo=Next.js&logoColor=white"/>
<img alt="Tawilwind CSS" src="https://img.shields.io/badge/Tailwind CSS-06B6D4.svg?style=for-the-badge&logo=TailwindCSS&logoColor=white"/>
<img alt="Redux" src="https://img.shields.io/badge/Redux-764ABC.svg?style=for-the-badge&logo=Redux&logoColor=white"/>
<img alt="Axios" src="https://img.shields.io/badge/Axios-5A29E4.svg?style=for-the-badge&logo=Axios&logoColor=white"/>

**Main-Server**  
<img alt="Go" src="https://img.shields.io/badge/Go-00ADD8.svg?style=for-the-badge&logo=Go&logoColor=white"/>
<img alt="Amazon S3" src="https://img.shields.io/badge/AmazonS3-569A31.svg?style=for-the-badge&logo=AmazonS3&logoColor=white"/>
<img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1.svg?style=for-the-badge&logo=PostgreSQL&logoColor=white"/>
<img alt="JSON Web Tokens" src="https://img.shields.io/badge/JSONWebTokens-000000.svg?style=for-the-badge&logo=JSONWebTokens&logoColor=white"/>
<img alt="SQLC" src="https://img.shields.io/badge/sqlc-000000.svg?style=for-the-badge&logo=sqlc&logoColor=white"/>  

**Contract-Server**  
<img alt="Node.js" src="https://img.shields.io/badge/Node.js-339933.svg?style=for-the-badge&logo=Node.js&logoColor=white"/>
<img alt="Express" src="https://img.shields.io/badge/Express-000000.svg?style=for-the-badge&logo=Express&logoColor=white"/>
<img alt="Web3.js" src="https://img.shields.io/badge/Web3.js-F16822.svg?style=for-the-badge&logo=Web3.js&logoColor=white"/>
<img alt="IPFS" src="https://img.shields.io/badge/IPFS-65C2CB.svg?style=for-the-badge&logo=IPFS&logoColor=white"/>
<img alt="MySQL" src="https://img.shields.io/badge/MySQL-4479A1.svg?style=for-the-badge&logo=MySQL&logoColor=white"/>
<img alt="Sequelize" src="https://img.shields.io/badge/Sequelize-52B0E7.svg?style=for-the-badge&logo=Sequelize&logoColor=white"/>

**Etc**  
<img alt="Solidity" src="https://img.shields.io/badge/Solidity-363636.svg?style=for-the-badge&logo=Solidity&logoColor=white"/>
<img alt="npm" src="https://img.shields.io/badge/npm-CB3837.svg?style=for-the-badge&logo=npm&logoColor=white"/>
<img alt=".ENV" src="https://img.shields.io/badge/.ENV-ECD53F.svg?style=for-the-badge&logo=.ENV&logoColor=white"/>
<img alt="Discord" src="https://img.shields.io/badge/Discord-5865F2.svg?style=for-the-badge&logo=Discord&logoColor=white"/>
<img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED.svg?style=for-the-badge&logo=Docker&logoColor=white"/>
<img alt="Ganache" src="https://img.shields.io/badge/Ganache-E25A1C.svg?style=for-the-badge&logo=Ganache&logoColor=white"/>

### Next.js

Next.js는 리액트를 위해 만든 **오픈소스 자바스크립트 웹 프레임워크**로, 리액트에는 없는 **서버 사이드 렌더링(Server Side Rendering, SSR), 검색 엔진 최적화(Search Engine Optimization)**이 가능하다.

- **클라이언트 사이드 렌더링(Client Side Rendering, CSR)**
    - 리액트에서 쓰이는 **클라이언트 사이드 렌더링(Client Side Rendering, CSR)**의 경우 모든 자바스크립트 파일을 로드하고 사용자는 웹을 보게 되는데 이때까지 사용자는 많은 시간을 대기해야 한다. 또, 자바스크립트가 로드 되지 않은 경우 아무런 정보를 보이지 않는다. 구글의 검색 엔진의 경우 자바스크립트가 로드 되지 않은 페이지를 검색 엔진으로 스캔함으로 결론적으로 검색에 아무 페이지도 걸리지 않게 된다.
- **서버 사이드 렌더링(Server Side Rendering, SSR)**
    - **서버 사이드 렌더링(Server Side Rendering, SSR)**은 서버에서 자바스크립트를 로딩함으로써 클라이언트 측에서는 자바스크립트를 로딩하는 시간이 줄어들게 된다. 그리고 검색 엔진이 자바스크립트를 읽는 것이 아닌 서버측에서 자바스크립트, html, css를 만들어 컨텐츠에 직접 업로드 함으로 검색 엔진에 게시글이 걸리게 된다. 또한 meta 태그를 자유롭게 추가함으로 SEO를 용이하게 할 수 있다.

### Redux

- 애플리케이션의 state를 관리하기 위한 오픈소스 JavaScript 라이브러리이다.
- Redux는 원리가 간단하고 모든 수정 사항을 기록한다.
- 모든 히스토리가 기록되어 에러 추적이 쉽고 안정적이다.
- 앱이 커지면 코드를 쪼개야 하는데 Reducer들을 쪼갤 수 있어 편리하다. (Reducer는 전달 받은 action에 따라 상태를 어떻게 업데이트 할지 정의한 함수)
- Redux를 사용하면 애플리케이션 전체에 걸쳐 상태를 공유할 수 있다. 이는 React의 prop drilling 문제를 해결하는 데 도움이 된다.

### Tailwind CSS

Tailwind CSS는 HTML 파일, JavaScript 컴포넌트와 클래스네임을 위한 다른 템플릿 모두를 스캐닝해서 대응하는 스타일을 생성하고 그것들을 정적인 CSS 파일에 입력하여 동작한다.

제로 런타임으로 동작하며 빠르고, 유연하며 믿을 수 있다.

- CSS를 작성할 때 시간을 많이 절약할 수 있다.
- 컴포넌트 생성과 관리가 쉬우며, 유지 보수하기 편하다.
- 프로그래밍 언어와 같은 추상화 수준을 제공해 스타일을 빠르게 적용할 수 있어 코드의 길이가 줄고, 개발 시간이 절약된다.
- 커스터마이징이 쉬워 원하는 대로 디자인을 변경할 수 있다.
- 반응형 디자인 구현도 쉽다.
- 클래스에 유틸리티한 이름(flex, pt-4, ...)을 붙여 HTML 내에서 개발하는 방식이다.

## 구현

### 메인 페이지

![MainPage](../../assets/img/codestates/plohub/mainPage.gif){:.centered}
*메인 페이지 화면*

메인 페이지는 유저들이 작성한 게시글 목록이 보이며, 왼쪽의 메뉴 토글 버튼을 클릭하면 카테고리가 보인다. 카테고리를 클릭하면 클릭한 카테고리에 해당하는 게시글이 보이도록 구현했다.  
또한 메인 페이지의 게시글 리스트는 페이지 초기 렌더링 시 서버 측에서 데이터를 가져와서 해당 데이터와 함께 페이지를 렌더링 할 수 있다고 판단해 SSR을 적용했다.

```jsx
/**
 * 서버 사이드 렌더링(SSR)을 위한 함수
 * 페이지, 제한값, 카테고리를 쿼리 파라미터로 받아 백엔드에서 게시물 리스트를 가져옴
 * 
 * @param {object} context - Next.js의 context 객체. 쿼리 파라미터 등 서버 사이드 렌더링에 필요한 정보를 담고 있음
 * @returns {object} props - 컴포넌트로 전달될 props. 게시물 리스트를 포함
 */
export const getServerSideProps = async ({ query }) => {
    const page = query.page || 1; // Default page is 1
    const limit = query.limit || 10; // Default limit is 10
    const { category } = query;

    try {
        const res = await axios.get(`${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/list`, {
            params: {
            page,
            limit,
            category,
            },
            withCredentials: true
        });
    
        const postList = res.data.posts;

        return {
            props: {
                postList,
            }
        };
        } catch (error) {
        console.error('게시물을 가져오는데 실패했습니다:', error);
    
        return {
            props: {
                postList: null,
            }
        };
    }
};
```
*게시글 리스트 SSR 코드*

### 회원 가입

![SignUp](../../assets/img/codestates/plohub/signup.gif){:.centered}  
*회원가입 화면*  

회원 가입 시 서버로 중복된 이메일이 있는지 체크를 하고, 중복된 이메일이 있을 경우 에러 문구를 띄워주도록 구현했다.  
비밀번호는 영어 대소문자, 숫자, 특수 기호가 포함되어야 하며 최소 8자 이상으로 조건을 정했는데, 이 조건이 지켜지지 않을 시 `SignUp` 버튼 클릭은 불가능하다.

```jsx
/**
 * 이메일 확인을 위한 함수
 *
 * @async
 * @function emailConfirm
 * @returns {Promise<void>} Promise 객체
 * @throws {Error} 이메일 확인 중 발생한 오류
 */
    const emailConfirm = async () => {
        const formData = new FormData();

        formData.append('email', email);

        try {
            const response = await axios.post(
                `${process.env.NEXT_PUBLIC_BACKEND_URL}/users/check-email`,
                { email }, // 요청 데이터를 JSON 객체로 전달
                {
                headers: {
                    "Content-Type": "application/json", // Content-Type을 application/json으로 설정
                    "Accept": "application/json",
                },
                }
            );
            if (response.data.status === 200) {
                setEmailValidated(true);
                setIsModalOpen(true);
                setModalTitle('Success');
                setModalBody('이 이메일은 사용 가능합니다.');

                setTimeout(() => {
                    setIsModalOpen(false);
                }, 3000);
            } else {
                setEmailValidated(false);
                setIsModalOpen(true);
                setModalTitle('Error');
                setModalBody('오류가 발생했습니다.');

                setTimeout(() => {
                    setIsModalOpen(false);
                }, 3000);
            }
        } catch (error) {
            console.log('Error', error.message);
            if (error.response && error.response.status === 400) {
                setEmailValidated(false);
                setIsModalOpen(true);
                setModalTitle('Error');
                setModalBody(error.message);
                document.getElementById('confirm-email').style.display = 'block';

                setTimeout(() => {
                    setIsModalOpen(false);
                }, 3000);
            } else {
                alert("서버 에러가 발생했습니다. 잠시 후 다시 시도해주세요.");
            }
        }
    }
```
*이메일 중복 체크 코드*  

```jsx
/**
 * 비밀번호 유효성 검사를 수행하는 함수
 * - 비밀번호는 최소 8자 이상이어야 하며,
 * - 대문자, 소문자, 숫자, 특수기호가 모두 포함되어야 함
 */
const validatePassword = () => {
    const passwordRegex = /^(?=.*[!@#$%^&*])(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$/;
    if (password.length < 8) {
        setPasswordError('비밀번호는 최소 8자 이상이어야 합니다.');
    } else if (!passwordRegex.test(password)) {
        setPasswordError('비밀번호는 영문 대문자, 영문 소문자, 숫자, 특수기호를 모두 포함해야 합니다.');
    } else {
        setPasswordError('');
    }
};

/**
 * 비밀번호 확인 유효성 검사를 수행하는 함수
 * - 비밀번호 확인 입력값이 비어있지 않아야 하며,
 * - 비밀번호 입력값과 비밀번호 확인 입력값이 동일해야 함
 */
const passwordConfirm = () => {
    if (pwConfirm.length === 0) {
    }
    if (password.length <= 0 && pwConfirm.length <= 0 ) {
        setPwConfirmError('');
        setPwConfirmMessage('');
    } else if (password === pwConfirm) {
        setPwConfirmMessage('비밀번호가 일치합니다.');
        setSignUpDisabled(false);
        setPwConfirmError('');
    } else if (password !== pwConfirm) {
        setPwConfirmError('비밀번호가 일치하지 않습니다.');
        setPwConfirmMessage('');
    }
}
```
*비밀번호 유효성 검사 코드*

```jsx
/**
 * 회원 가입을 처리하는 함수.
 *
 * @async
 * @function signUp
 * @returns {Promise<void>} Promise 객체
 * @throws {Error} 회원 가입 중 발생한 오류
 */
const signUp = async () => {
    const formData = new FormData();

    formData.append('email', email);
    formData.append('password', password);

    try {
        let response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/users/signup`, formData, {
            headers: {
                "Content-Type": "multipart/form-data",
                "Accept": "application/json",
            },
        });
        if (response.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody(response.data.message);

            setTimeout(() => {
                setIsModalOpen(false);
                router.push('/users/signin');
            }, 3000);
        }
    } catch (error) {
        console.log('Error', error.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000)
    }
}
```
*회원가입 코드*

### 로그인

![SignUp](../../assets/img/codestates/plohub/login.gif)
*로그인 화면*  

로그인을 하지 않은 상태로 메인 페이지의 `글쓰기` 버튼을 클릭할 경우 `로그인이 필요합니다.`라는 문구가 모달로 띄워지도록 구현했다.  
로그인이 완료되면 메인 페이지로 자동으로 이동이 된다.  

```jsx
/**
 * 행동을 진행하기 전에 사용자가 로그인했는지 확인
 * 사용자가 로그인하지 않은 경우, 기본 동작을 방지하고 사용자에게 알리는 모달을 띄움
 *
 * @param {Event} e - 로그인 확인을 트리거한 이벤트.
 */
const loginCheck = (e) => {
    
    if (user.email === '') {
        e.preventDefault();
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody('로그인이 필요합니다.');
        
        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}
```
*로그인 체크 코드*

```jsx
/**
 * 사용자 로그인을 처리하는 비동기 함수
 * 사용자의 이메일과 비밀번호를 사용하여 서버에 로그인 요청을 보내며,
 * 응답이 성공적인 경우, 사용자 정보를 받아와 Redux Store에 저장하고,
 * 홈 화면으로 이동하게 됨, 만약 요청이 실패한 경우, 오류 메시지를 모달로 표시
 * 모든 모달은 자동적으로 3초 후에 닫히게 됨
 */
const signIn = async () => {
    const formData = new FormData();

    formData.append('email', email);
    formData.append('password', password);

    try {
        let response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/users/login`, formData, {
            headers: {
                'Content-Type': 'multipart/form-data',
                'Accept': 'application/json'
            },
            withCredentials: true // Add this line
        });
        if (response.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('로그인 되었습니다.');

            const { email, nickname, level, address, eth_amount, token_amount, daily_token } = response.data.user_info;
            const { access_token } = response.data;

            dispatch({ type: SET_EMAIL, payload: email });
            dispatch({ type: SET_ADDRESS, payload: address });
            dispatch({ type: SET_NICKNAME, payload: nickname });
            dispatch({ type: SET_LEVEL, payload: level });
            dispatch({ type: SET_TOKEN_BALANCE, payload: token_amount });
            dispatch({ type: SET_DAILY_TOKEN_BALANCE, payload: daily_token });
            dispatch({ type: SET_ETH_BALANCE, payload: eth_amount });
            
            setTimeout(() => {
                setIsModalOpen(false);
                router.push('/');
            }, 3000);
        }
    } catch (error) {
        console.log('Error', error.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000)
    }
}
```
*로그인 코드*


### 게시글 작성

![PostCreate](../../assets/img/codestates/plohub/post_create_lv1.gif){:.centered}
*게시글 작성 화면 Lv.1*  
![PostCreate_2](../../assets/img/codestates/plohub/post_create.gif){:.centered}
*게시글 작성 화면*  
![PostCreate_2](../../assets/img/codestates/plohub/post_create_lv2.gif){:.centered}
*게시글 작성 화면 Lv.2*  

게시글 작성의 경우 유저의 등급에 따라 작성할 수 있는 카테고리가 나뉜다. 레벨 1인 경우 `코스 정보`를 제외한 `행사 정보`, `참여 후기`를 작성할 수 있고, 레벨 2인 경우에는 모든 카테고리에서 게시글 작성이 가능하다.
유저의 레벨은 서버에서 데이터를 받아 Redux를 사용하여 체크하도록 구현했다.  

```jsx
/**
 * 사용자 레벨을 확인하여 'courseinfo' 카테고리가 선택되었지만 
 * 사용자 레벨이 2가 아닌 경우 에러 메시지를 보여주는 함수
 */
const userLevelCheck = () => {
    if(user.level !== 2 && selectCategory === 'courseinfo') {
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody('해당 카테고리는 2레벨만 작성 가능합니다.');

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}

/**
 * selectCategory가 변경될 때마다 userLevelCheck 함수를 호출하여 사용자 레벨을 확인
 */
useEffect(() => {
    userLevelCheck()
}, [selectCategory]);
```
*카테고리 유저 레벨 체크*  

```jsx
/**
 * 사용자가 파일을 선택하면 이를 처리하는 함수
 * 이 함수는 선택한 파일의 확장자를 확인하고,
 * 확장자에 따라 이미지 또는 비디오를 각각의 상태에 저장
 * @param {Event} e - 파일 입력 이벤트 객체
 */
const handleFileChange = (e) => {
    const files = Array.from(e.target.files)

    files.forEach((file) => {
        const extension = file.name.split('.').pop().toLowerCase();
    
        if (extension === 'jpg' || extension === 'jpeg' || extension === 'png') {
            setImages((prevImages) => [...prevImages, file]);
        } else if (extension === 'mp4' || extension === 'avi' || extension === 'mov') {
            setVideos((prevVideos) => [...prevVideos, file]);
        }
    });
    setSelectedFile(files)
};

/**
 * 사용자가 작성한 제목, 내용, 카테고리, 이미지, 비디오를 이용하여 새 게시글을 생성하는 함수
 * 이 함수는 사용자가 제공한 정보를 FormData 객체에 저장하고,
 * 해당 객체를 이용하여 서버에 POST 요청을 보냄
 */
const createPost = async () => {
    const formData = new FormData();

    formData.append('title', title);
    formData.append('content', content);
    if (selectCategory === 'all') {
        formData.append('category', 0);
    } else if(selectCategory === 'eventinfo') {
        formData.append('category', 1);
    } else if (selectCategory === 'courseinfo') {
        formData.append('category', 2);
    } else if (selectCategory === 'review') {
        formData.append('category', 3);
    }

    images.forEach((image) => {
        formData.append('images', image);
    });

    videos.forEach((video) => {
        formData.append('videos', video);
    });
    
    try {
        let response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/create`, formData, {
            headers: {
                'Content-Type': 'multipart/form-data', // 파일 업로드 시 Content-Type 설정
            },
            withCredentials: true
        });

        if (response.data.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('게시글이 등록되었습니다.');

            setTimeout(() => {
                setIsModalOpen(false);
                router.push('/users/mypage');
            }, 3000);
        }
    } catch (e) {
        console.log('Error: ', e.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(e.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}
```
*게시글 생성 코드*

```jsx
<div className='w-full flex gap-3 justify-end mt-16'>
    <button className='
        w-[15%] 
        border 
        rounded-2xl 
        p-3 
        bg-blue-main 
        text-white 
        hover:bg-blue-dark 
        transition 
        duration-300'
        onClick={() => router.push('/')}>
        Cancel
    </button>
    <button className='
        w-[15%] 
        border 
        rounded-2xl 
        p-3 
        bg-blue-dark 
        text-white 
        hover:bg-blue-main 
        transition 
        duration-300'
        onClick={createPost}>
        Create
    </button>
</div>
```
*게시글 생성 취소 시 메인 페이지로 이동하는 코드*

### 게시글 상세 페이지

![PostDetail](../../assets/img/codestates/plohub/post_detail.gif)
*게시글 상세 페이지*  

게시글 상세 페이지의 경우 서버 측에서 `Amazon S3`를 사용하여 저장한 이미지를 불러올 수 있도록 구현했다.
게시글을 작성한 유저 본인일 경우 게시글 삭제가 가능하며, 본인이 아닐 경우 삭제 버튼은 보이지 않는다.  
게시글 상세 페이지의 경우에도 서버에서 가져온 데이터를 페이지와 함께 렌더링 할 수 있도록 SSR을 사용했다.

```jsx
/**
 * 서버 사이드 렌더링(SSR)을 위한 함수
 * 주어진 게시물 ID(pid)에 해당하는 게시물의 상세 정보들을 가져옴
 * 
 * @param {object} context - Next.js의 context 객체. 쿼리 파라미터, 쿠키 등 서버 사이드 렌더링에 필요한 정보를 담고 있음
 * @returns {object} - props 객체를 반환, 
 * 'postDetail' 키에는 게시물 상세 정보가 담겨 있음
 */
export const getServerSideProps = async ({ query }) => {
    const { pid } = query;

    try {
        const res = await axios.get(`${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/detail/${pid}`, {
            withCredentials: true
        });
    
        const postDetail = res.data;

        return {
            props: {
                postDetail,
            }
        };
        } catch (error) {
        console.error('게시물을 가져오는데 실패했습니다:', error);
    
        return {
            props: {
                postList: null,
            }
        };
    }
};
```
*게시글 상세 페이지 SSR 코드*

```jsx
/**
 * 게시글을 삭제하는 함수입니다. 삭제 성공 시 성공 메시지를, 
 * 실패 시 에러 메시지를 모달로 표시
 */
const deletePost = async () => {
    try {
        let response = await axios.delete(`${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/${postDetail.post_info.id}`, {
            withCredentials: true
        });
        
        if (response.data.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('게시글이 삭제되었습니다.');

            setTimeout(() => {
                setIsModalOpen(false);
                router.push('/');
            }, 3000);
        }
    } catch (error) {
        console.log('Error: ', error.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}
```
*게시글 삭제 코드*

```jsx
const isPostAuthor = user && user.email === postDetail.post_info.author.email;

{isPostAuthor && 
    <button className='
        w-28 
        h-12 
        rounded-xl 
        bg-red-400 
        hover:bg-red-500 
        text-white 
        text-white 
        transition 
        duration-300'
        onClick={deletePost}>
        Delete
    </button>
}
```
*저자 확인하여 게시글 삭제 버튼 구현 코드*


### 댓글 기능

![Comment](../../assets/img/codestates/plohub/comment.gif){:.centered}
*댓글 작성 후 토큰 보상*

게시글에 댓글을 작성 하면 토큰을 보상 받을 수 있으며, 마이페이지에서 확인이 가능하다. 
댓글은 작성자인 경우, 삭제 버튼이 보이고 작성자가 아닌 경우에는 삭제 버튼이 보이지 않는다.  

```jsx
/**
 * 새로운 댓글을 생성하는 함수
 * 게시글 ID와 댓글 내용을 서버에 POST 요청으로 보냄
 * 댓글 생성 성공 시 성공 메시지를, 실패 시 에러 메시지를 모달로 표시
 */
const createComment = async () => {
    const formData = new FormData();

    formData.append('post_id', postDetail.post_info.id);
    formData.append('content', comment);

    try {
        let response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/comments/create`, formData, {
            headers: {
                'Content-Type': 'multipart/form-data', // 파일 업로드 시 Content-Type 설정
            },
            withCredentials: true
        });

        if (response.data.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('댓글이 등록되었습니다.');
            
            setTimeout(() => {
                setIsModalOpen(false);
                setComment('');
                router.reload();
            }, 3000);
        }
    } catch (error) {
        console.log('Error: ', error.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}

/**
 * 댓글을 삭제하는 함수입니다. 삭제 성공 시 성공 메시지를, 실패 시 에러 메시지를 모달로 표시
 * @param {string} id - 삭제할 댓글의 ID
 */
const deleteComment = async (id) => {
    try {
        let response = await axios.delete(`${process.env.NEXT_PUBLIC_BACKEND_URL}/comments/${id}`, {
            withCredentials: true
        });

        if (response.data.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('댓글이 삭제되었습니다.');

            const updatedComments = comments.filter(comment => comment.id !== commentId);
            setComments(updatedComments);
            
            setTimeout(() => {
                setIsModalOpen(false);
                router.reload();
            }, 3000);
        }
    } catch (error) {
        console.log('Error: ', error.message);
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}
```
*댓글 생성 및 삭제 코드*

```jsx
/**
 * 서버 사이드 렌더링(SSR)을 위한 함수
 * 주어진 게시물 ID(pid)에 해당하는 게시물의 상세 정보와, 해당 게시물에 달린 댓글들을 가져옴
 * 
 * @param {object} context - Next.js의 context 객체. 쿼리 파라미터, 쿠키 등 서버 사이드 렌더링에 필요한 정보를 담고 있음
 * @returns {object} - props 객체를 반환, 
 * 'postDetail' 키에는 게시물 상세 정보가, 'commentList' 키에는 해당 게시물에 달린 댓글들의 목록이 담겨 있음
 */
export const getServerSideProps = async ({ query }) => {
    const { pid } = query;

    try {
        const res = await axios.get(`${process.env.NEXT_PUBLIC_BACKEND_URL}/posts/detail/${pid}`, {
            withCredentials: true
        });
    
        const postDetail = res.data;

        const res2 = await axios.get(`${process.env.NEXT_PUBLIC_BACKEND_URL}/comments/list/${postDetail.post_info.id}`, {
            withCredentials: true
        });

        const commentList = res2.data.comments;

        return {
            props: {
                postDetail,
                commentList
            }
        };
        } catch (error) {
        console.error('게시물을 가져오는데 실패했습니다:', error);
    
        return {
            props: {
                postList: null,
                commentList: null
            }
        };
    }
};
```
*댓글 리스트 SSR 코드*

### 토큰 전송

![TokenSend](../../assets/img/codestates/plohub/token_send.gif){:.centered}
*토큰 전송*  
![Change counterparty balance after token transfer](../../assets/img/codestates/plohub/token_send_amount.gif)
*토큰 전송 후 상대방 잔액 변화*

게시물 상세 페이지에서 유저의 닉네임을 클릭하면 해당 유저의 지갑 주소가 복사된다. 복사한 지갑 주소로 마이페이지에서 토큰 전송이 가능하다.

```jsx
/**
 * 토큰 전송을 처리하는 비동기 함수
 * 사용자가 입력한 주소와 토큰 양을 사용하여 서버에 토큰 전송 요청을 보내며,
 * 응답이 성공적인 경우, 토큰 전송 성공 메시지를 모달로 표시하고 페이지를 새로 고침
 * 만약 요청이 실패한 경우, 오류 메시지를 모달로 표시
 * 모든 모달은 자동적으로 3초 후에 닫히게 됨
 */
const tokenSend = async () => {
    const token = cookie.parse(document.cookie || '');
    const formData = new FormData();

    formData.append('to_address', toAddr);
    formData.append('token_amount', tokenAmount);

    try {
        const response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/token/transfer`, formData, {
            headers: {
                'Authorization': `Bearer ${token}`
            },
            withCredentials: true
        });

        if (response.status === 200) {
            setModalOpen(true);
            setModalTitle('Success');
            setModalBody('토큰 전송이 완료되었습니다.');

            setTimeout(() => {
                setModalOpen(false);
                router.reload();
            }, 3000);
        }
    } catch (error) {
        console.log('Error', error.message);
        setModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setModalOpen(false);
        }, 3000);
    }
}
```
*토큰 전송 코드*

### 토큰 스왑

![Token Swap](../../assets/img/codestates/plohub/token_swap.gif){:.centered}
*토큰 -> ETH 교환*

마이 페이지에서 토큰 교환 버튼을 클릭하면 토큰을 ETH로 교환할 수 있는 모달 창이 뜬다.  
교환하고 싶은 토큰의 수량을 입력하면 토큰과 이더의 비율을 계산하여 토큰의 수량에 비례한 이더의 양이 자동으로 입력이 된다.

```jsx
/**
 * 사용자가 입력한 토큰의 양에 따라 상응하는 이더리움의 양을 계산하고 설정하는 함수
 * 이 함수는 입력 이벤트에서 호출되며, 토큰과 이더리움의 교환 비율을 기반으로 계산
 * 이 경우, 토큰 1000개당 이더리움 1개로 계산
 *
 * @param {object} e - 이벤트 객체
 */
const tokenAmountChange = (e) => {
    const inputTokenAmount = e.target.value;
    setTokenAmount(inputTokenAmount);

    // 토큰 스왑 비율 계산
    const tokenToEthRatio = 1000; // 토큰 1000개당 이더 1개로 가정
    const calculatedEthAmount = inputTokenAmount / tokenToEthRatio;
    setEthAmount(calculatedEthAmount);
};

/**
 * 토큰과 이더리움 간의 교환을 처리하는 비동기 함수
 * 사용자가 입력한 토큰 양을 사용하여 서버에 토큰 교환 요청을 보내며,
 * 응답이 성공적인 경우, 토큰 교환 성공 메시지를 모달로 표시하고 페이지를 새로 고침
 * 만약 요청이 실패한 경우, 오류 메시지를 모달로 표시
 * 모든 모달은 자동적으로 3초 후에 닫히게 됨
 */
const tokenSwap = async () => {
    const formData = new FormData();
    const token = cookie.parse(document.cookie || '');

    formData.append('token_amount', tokenAmount);

    try {
        const response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/token/swap`, formData, {
            headers: {
                'Authorization': `Bearer ${token}`
            },
            withCredentials: true
        });

        if (response.status === 200) {
            setModalOpen(true);
            setModalTitle('Success');
            setModalBody('토큰 교환이 완료되었습니다.');

            setTimeout(() => {
                setModalOpen(false);
                router.reload();
            }, 3000);
        }
    } catch (error) {
        console.log('Error', error.message)
        setModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setModalOpen(false);
        }, 3000);
    }
}
```
*토큰 스왑 코드*  

### NFT 민팅

![NFT Minting](../../assets/img/codestates/plohub/NFT_minting.gif){:.centered}
*NFT 민팅*

유저가 소유하고 있는 토큰의 수량이 20개 이상인 경우 NFT 민팅이 가능하다.  
이미지와 이름, 설명 등을 입력 후 민팅 버튼을 클릭하면 Spinner와 함께 민팅이 되었다는 모달이 뜨며 바로 마이 페이지로 이동하여 민팅된 NFT를 확인할 수 있다.  
NFT의 가격 또한 20 PH(토큰) 이다.


```jsx
/**
 * NFT를 민팅하는 함수
 * 사용자가 입력한 이름(name), 설명(desc), 그리고 업로드한 파일(uploadFile)을 사용하여 민팅을 진행
 * 민팅이 진행되는 동안 모달을 열어 민팅 상태를 사용자에게 알림
 * 민팅이 성공적으로 완료되면 성공 메시지를 표시하고, 
 * 일정 시간 후에 사용자의 마이페이지로 리다이렉트
 * 민팅이 실패하면 오류 메시지를 표시
 */
const minting = async () => {
    const formData = new FormData();

    formData.append('name', name);
    formData.append('description', desc);
    formData.append('image', uploadFile);

    setIsModalOpen(true);
    setModalTitle('Minting');
    setModalBody(<FaSpinner size={50} className="animate-spin" />);

    try {
        const response = await axios.post(`${process.env.NEXT_PUBLIC_BACKEND_URL}/nft/mint`, formData, {
            withCredentials: true,
        });

        if (response.status === 200) {
            setIsModalOpen(true);
            setModalTitle('Success');
            setModalBody('민팅되었습니다.');

            setTimeout(() => {
                setIsModalOpen(false);
                router.push('/users/mypage');
            }, 3000);
        }
        if (response.status === 200) {

        }
    } catch (error) {
        console.log('Error', error.message)
        setIsModalOpen(true);
        setModalTitle('Error');
        setModalBody(error.message);

        setTimeout(() => {
            setIsModalOpen(false);
        }, 3000);
    }
}
```
*NFT Minting 코드*

### NFT 상세 페이지

![NFT Detail](../../assets/img/codestates/plohub/NFT_detail.gif){:.centered}
*NFT 상세 페이지*

현재 우리는 NFT 거래는 구현하지 않아 마이 페이지에서만 민팅된 NFT를 확인할 수 있다.  
NFT 카드를 클릭하면 해당 NFT에 대한 상세 페이지로 이동하며 이미지와 이름, 설명, 민팅 날짜, 지갑 주소 등을 확인할 수 있다.  

```jsx
/**
 * 서버 사이드 렌더링(SSR)을 위한 함수
 * 주어진 NFT ID(pid)에 해당하는 NFT의 상세 정보를 가져옴
 * 또한 사용자가 로그인 상태가 아니면 로그인 페이지로 리디렉션
 * 
 * @param {object} context - Next.js의 context 객체. 쿼리 파라미터, 쿠키 등 서버 사이드 렌더링에 필요한 정보를 담고 있음
 * @returns {object} - props 객체를 반환 'nftInfo' 키에는 NFT 상세 정보가 담겨 있음
 */
export const getServerSideProps = async (context) => {
    const { pid } = context.query;
    const cookies = cookie.parse(context.req.headers.cookie || '');
    let nftInfo;
    if (!cookies.access_token) {
        return {
            redirect: {
                destination: '/users/signin',
                permanent: false,
            },
        }
    }

    try {
        const response = await axios.get(`${process.env.NEXT_PUBLIC_BACKEND_URL}/nft/detail/${pid}`, {
            withCredentials: true
        });

        nftInfo = response.data.nft;
    } catch (error) {
        console.log('Error', error.message)
    }
    
    return {
        props: { nftInfo },
    }
}
```
*NFT 상세 페이지 SSR 코드*


## 마무리
이렇게 두 번째 프로젝트도 마무리가 됐다. 앞서 말했듯이 이번에는 처음부터 규칙과 기획을 확실하게 정하고 프로젝트를 시작해서 첫 번째 프로젝트에 비해 수월했다. 정규 시간이 끝난 후에도 조금씩 부지런히 프로젝트를 진행하다 보니 밤샐 일도 없이 기간에 딱 맞게 끝낼 수 있었다. 완전한 완성이라고는 볼 수 없지만, 그래도 기간에 비해 많이 했다고 생각해 좀 뿌듯한 감정도 있다.  
이번에는 팀장님이 `Next.js`를 사용을 할 수 있느냐 라고 먼저 물어봐주셔서 감사했다. 안그래도 `SSR`을 써보고 싶었는데 혼자서는 어떻게 해야 할지 막막해 그저 생각만 하고 속에 담아만 두고 있던 상태였었는데, 먼저 제안을 해주셔서 바로 승낙하고 이번 프로젝트에 적용을 시킬 수 있었다. CSS 라이브러리는 `Tailwind CSS`와 `Chakra UI` 중 고민이 많았는데 선호도가 `Tailwind CSS`가 더 높은 것 같고 위에 작성한 특징들을 보고 결정하게 되었다. 처음에는 Docs랑 계속 왔다갔다 하며 진행해서 조금 시간이 걸렸던 것 같은데, 사용하는 것이 일정하다 보니 나중에는 조금 외워서 금방 코드를 작성할 수 있어서 좋았다. 게다가 반응형도 완벽하지는 않지만 어느 정도 작동을 해서 좋은 라이브러리인 것 같다. 세 번째 프로젝트에서도 사용을 할 지는 잘 모르겠지만 고려는 해볼만 한 것 같다.  
그리고 이번에 팀장님의 캐리로 `Docker`까지 사용을 해봤는데 정말 편리했다. 아직 뭐가 뭔지는 잘은 모르지만, 컨테이너를 실행하면 팀장님이 설정해주신 서버들이 모두 한 번에 실행이 되며, 로그까지 같이 볼 수 있고 각자 컴퓨터의 환경 설정과 관계 없이 실행할 수 있다는 점이 가장 큰 장점 같다. 여러 회사에서도 `Docker`를 꽤나 사용하고 있으니 나도 좀 더 공부해서 실행되는 과정과 설정들을 좀 익혀야 될 필요성을 느꼈다.  
세 번째 프로젝트는 드디어 마지막 프로젝트인데, 이번 프로젝트에서 진행한 팀원들과 첫 번째 프로젝트에서 같이 진행했던 한 분과 같이 마지막 프로젝트를 진행하게 되었는데 나는 개인적으로 나만의 드림팀이다.! 진짜로, 다들 잘하시는 분들만 모여서 마지막 프로젝트는 꽤나 기대된다.  


---
> [Git Hub Repository](https://github.com/codestates-beb/beb-09-PloHub)

