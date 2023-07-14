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
### 회원 가입

![SignUp](../../assets/img/codestates/plohub/signup.gif){:.centered}  

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


**작성 진행중....**

<!-- > 슬라이드 구현

![메인슬라이드](../../assets/img/codestates/firstSlide.png){:.centered}
*메인 슬라이드*  
![하단슬라이드](../../assets/img/codestates/secondSlide.png){:.centered}
*하단 슬라이드*  
랜딩 페이지의 슬라이드는 `react-slick` 라이브러리를 사용하여 구현했다.  
슬라이드 안의 이미지는 민팅이 완료된 NFT 이미지들이다. 이미지는 `IPFS`에 저장이 되는데 우리는 DB를 따로 사용하지 않아 IPFS의 메타데이터를 직접 가져오는 방법을 써야 했다.

```jsx
/**
   * 사용자의 토큰 목록을 가져오는 비동기 함수.
   * 
   * @async
   * @throws {Error} 토큰 목록을 가져오는 중 에러가 발생한 경우.
   * @returns {void} 토큰 목록을 설정하고 상태에 저장다.
   */
  const getUserToken = async () => {
    let contractAddress = process.env.REACT_APP_ERC_721_ADDRESS;

    try {
      // const response = await get721Contract(contractAddress).methods.getNftTokenList(user.account).call();
      const response = await get721Contract(contractAddress).methods.getAllNftList().call();
      console.log('response', response)
      // setNftList(prevList => [...prevList, ...response]);
      setNftList(response.map(nft => [Number(nft[0]), nft[1]]));
    } catch (error) {
      console.error(error);
    }
  }
  
  useEffect(() => {
    getUserToken()
  }, []);

  /**
   * 주어진 URL을 IPFS 주소로 변환하는 함수.
   * 
   * @param {string} url 변환할 URL.
   * @returns {string | undefined} IPFS 주소로 변환된 URL입니다. URL이 주어지지 않은 경우 `undefined`를 반환.
   */
  const IpfsParser = (url) => {
    const cid = url.slice(7,url.length)
    const ipfsUrl = "https://ipfs.io/ipfs/" + cid
    console.log(ipfsUrl)
    return ipfsUrl
  }
    
  /**
   * 모든 NFT 데이터를 가져오는 비동기 함수.
   * 
   * @async
   * @throws {Error} 데이터를 가져오는 중 에러가 발생한 경우.
   * @returns {void} NFT 데이터를 설정하고 상태에 저장.
   */
  useEffect(() => {
    const fetchData = async (url) => {
        try {
          const response = await fetch(IpfsParser(url));
          const data = await response.json();
          setInfoNft(prevList => [...prevList, ...(Array.isArray(data) ? data : [data])]);
          // return data;  
        } catch (error) {
            console.error(error);
        }
      };
  
    const fetchAllData = async () => {
      try {
        const allData = await Promise.all(NftList.map(data => fetchData(data[1])));
        setJsonData(allData);  // allData는 'image' 속성의 값의 배열입니다.
        console.log('jsonData', allData);
      } catch (error) {
          console.error(error);
      }
      };
  
      fetchAllData();
    }, [NftList]);
```
*생성된 NFT 정보를 가져오는 함수*
우선 우리가 배포한 컨트랙트를 이용해 생성된 NFT를 모두 받아오고 `useState`를 사용하여 데이터를 저장했다. `useState`에 저장한 데이터 중 image url만 받아와 `IpfsParser` 함수를 만들어 주어진 URL을 IPFS 주소로 변환하여 이미지를 출력했다.
메인 슬라이드의 이미지만 NFT 이미지이고, 하단 슬라이드의 이미지는 Dummy 이미지이다.

> Create Page

![CreatePage](../../assets/img/codestates/createPage.png)  
*Create Page*  
민팅 페이지는 생성할 NFT의 정보를 입력할 수 있는데, 필수 항목으로 이미지와 NFT의 타이틀, 가격을 입력하지 않으면 생성할 수 없도록 예외 처리를 했다.  


![이미지가 없을 경우](../../assets/img/codestates/file.png){: width="350" height="350"} | ![타이틀을 입력하지 않았을 경우](../../assets/img/codestates/title.png){: width="350" height="350"} | ![가격을 입력하지 않았을 경우](../../assets/img/codestates/price.png){: width="350" height="350"}


*각 필수 항목을 입력하지 않았을 경우 경고 화면*
*각 이미지를 클릭하면 크게 볼 수 있습니다.*

각 항목들을 모두 입력한 후 `Mint` 버튼을 클릭하면 민팅을 진행할 수 있다.  
서명 요청을 하면 서버에서 서명을 검증을 하게 된다. 검증이 완료되면 가스비를 지불할 수 있는 창이 뜨며, 가스비까지 지불이 완료되면 민팅이 완료된다.
민팅이 완료되면, 자동으로 마이페이지로 이동하여 민팅한 NFT를 바로 확인할 수 있다.


![Signature](../../assets/img/codestates/signature.png) | ![GasFee](../../assets/img/codestates/gasFee.png)


*서명 요청, 가스비 지불 창*
*각 이미지를 클릭하면 크게 볼 수 있습니다.*

```jsx
/**
   * 주어진 메타데이터 URL을 사용하여 비동기적으로 새 NFT 토큰을 발행다.
   *
   * @async
   * @param {string} metadata_url - 토큰 메타데이터의 URL.
   * @throws {Error} 토큰 발행 중 에러가 발생한 경우.
   * @returns {void} 토큰 발행이 성공하면 '/mypage'로 이동
   */
  const mintToken = async (metadata_url) => {
    let minter = user.account;
    let lastTokenId = tokenId;
    let tokenURI = metadata_url;
    let zeroWord = '0x0000000000000000000000000000000000000000000000000000000000000000';
    let gasPrice = await web3.eth.getGasPrice();
    let contractAddress = process.env.REACT_APP_ERC_721_ADDRESS;
  
    try {
      const receipt = await get721Contract(contractAddress).methods.mintNFT(tokenURI).send({
        from: minter,
        gasPrice: gasPrice,
        gasLimit: 500000
      });
  
      console.log('ERC_721 Success!');
      navigate('/mypage'); 
      setIsModalOpen(true);
      setMessage('Minting completed.');
      setTimeout(() => {
        setIsModalOpen(false);
        setMessage('');
      }, 5000);
    }
    catch (e) {
      console.log(e);
      setModalTitle('Error');
      setMessage(e.message); // Set the error message here
      setIsModalOpen(true);  // And open the modal with the error
      setLoading(false);  // Stop loading
    }
  }
  
  /**
   * NFT 토큰을 발행하는 비동기 함수다.
   *
   * @async
   * @throws {Error} 파일, 타이틀, 가격 중 하나라도 입력하지 않은 경우, 또는 토큰 발행 중 에러가 발생한 경우.
   * @returns {void} 발행이 성공하면 토큰 ID를 1 증가시키고 토큰 발행 함수(mintToken)를 호출합니다.
   */
  const mint = async () => {
    
    if(nftItem == null) { 
      setModalTitle('Error');
      setMessage('파일을 선택해 주세요.'); 
      setIsModalOpen(true); 
    } else if (title.length === 0) {
      setModalTitle('Error');
      setMessage('타이틀을 입력해 주세요.'); 
      setIsModalOpen(true); 
    } else if (price.length === 0) {
      setModalTitle('Error');
      setMessage('가격을 입력해 주세요.'); 
      setIsModalOpen(true); 
    } else {

      // 민팅 중 상태로 설정
      setLoading(true); 
      setModalTitle('Minting');
      setMessage('Minting...'); 
      setIsModalOpen(true); 
      let from = user.account;
      let params = [localStorage.getItem('Sign'), from];
      let method = 'personal_sign'
      console.log(params);
      try {
        web3.currentProvider.sendAsync({
          method,
          params,
          from
        }, function (err, result) {
          if (!err) {
            const signature = result.result;
  
            const formData = new FormData();
            formData.append('img', nftItem);
            formData.append('title', title);
            formData.append('exLink', externalLink);
            formData.append('description', description);
            formData.append('category', category);
            formData.append('price', price);
            formData.append('signature', signature);
            formData.append('message', localStorage.getItem('Sign'));
            formData.append('userAddress', user.account);
  
            axios(`http://localhost:8082/create`, {
              method: 'POST',
              data: formData,
              headers: {
                'Content-Type': 'multipart/form-data',
                'Accept': '*/*',
              }
            }).then(res => {
              console.log(res);
              // Here you can call the mintToken function and pass the metadata url.
              let metadata_url = res.data.resultUri; // assuming this is the format of the response
  
              mintToken(metadata_url);
              setTokenId(tokenId + 1);    // 토큰이 발행된 후 토큰 ID 증가
            })
          }
        })
      } catch (error) {
        console.log(error);
        setModalTitle('Error');
        setMessage(error.message); // Set the error message here
        setIsModalOpen(true);  // And open the modal with the error
        setLoading(false);  // Stop loading
      }
    }
  }
```
*Mining 코드*

> My Page


![MyPage](../../assets/img/codestates/MyPage.png)


*My Page*

마이 페이지에서는 내가 발행하고 소유한 NFT 리스트를 볼 수 있다. 또한 나의 지갑 주소도 확인할 수 있다.
지갑 주소는 `Header`에서 로그인한 지갑 주소를 가져오는 것인데, `props`로 던져주는 방식이 아닌 `Context` 상태 관리 라이브러리를 사용했다.
일반적으로 React 애플리케이션에서 데이터는 위에서 아래로 (즉, 부모로부터 자식에게) props를 통해 전달되지만, 애플리케이션 안의 여러 컴포넌트들에 전해줘야 하는 `props`의 경우 이 과정이 번거로울 수 있다. `Context`를 이용하면, 트리 단계마다 명시적으로 `props`를 넘겨주지 않아도 많은 컴포넌트가 이러한 값을 공유할 수 있도록 할 수 있다.
```jsx
// Context 폴더 ActionTypes.js

export const SET_ACCOUNT = "SET_ACCOUNT";
export const SET_PROFILE = "SET_PROFILE";
export const SET_BANNER = "SET_BANNER";
export const SET_BALANCE = "SET_BALANCE";
export const SET_LOGOUT = "SET_LOGOUT";
```
*사용할 변수 설정*  

```jsx
// Context 폴더 index.js

import { createContext, useReducer } from "react";
import { SET_ACCOUNT, SET_BALANCE, SET_LOGOUT, SET_PROFILE, SET_BANNER } from "./ActionTypes";

// 초기 상태
//initial state
const initialState = {
  user: {
    account: '',
    balance: '',
    name: '',
    profile: '',
    banner: '',
  }
};

// Context 생성
/**
 * 빈 객체를 기본값으로 가지는 새로운 Context를 생성.
 * @type {React.Context<{}>}
 */
const Context = createContext({});    // 빈 객체가 기본값

/**
 * 사용자의 데이터를 관리하기 위한 리듀서 함수.
 * 
 * @param {Object} state - 현재 상태.
 * @param {Object} action - 수행할 액션을 나타내는 객체. `type`과 `payload`를 포함.
 * 
 * @returns {Object} 새로운 상태.
 * 
 * @case {SET_LOGOUT} 모든 사용자 데이터를 초기 상태로 재설정.
 * @case {SET_ACCOUNT} 사용자 데이터 중 `account`를 업데이트.
 * @case {SET_PROFILE} 사용자 데이터 중 `profile`을 업데이트.
 * @case {SET_BANNER} 사용자 데이터 중 `banner`를 업데이트.
 */
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case SET_LOGOUT:
            return {
              ...state,
              user: {
                account: '',
                balance: '',
                name: '',
                profile: '',
                banner: '',
              },
            }
    case SET_ACCOUNT:
        return {
          ...state,
          user: {
            ...state.user,
            account: action.payload
          }
        }
    case SET_BALANCE:
      return {
        ...state,
        user: {
          ...state.user,
          balance: action.payload
        }
      }

    case SET_PROFILE:
      return {
        ...state,
        user: {
          ...state.user,
          profile: action.payload
        }
      }

    case SET_BANNER:
        return {
          ...state,
          user: {
            ...state.user,
            banner: action.payload
          }
        }
  }
}

// value 객체를 Context.Provider에 제공, value 객체는 state와 dispatch를 포함
/**
 * @param {Object} props - 자식 요소를 props로 받음
 * @returns {Object} Context.Provider - value 값을 가진 Context.Provider를 반환, value는 state와 dispatch를 포함한 객체
 * 
 * @function useReducer
 * @param {function} reducer - 상태를 변환하는 데 사용되는 reducer 함수
 * @param {object} initialState - 초기 상태 값
 * @returns {Array} state와 dispatch - 현재 상태와 상태를 업데이트하는 dispatch 함수를 반환
 */
const Provider = ({ children }) => {
  // reducer 함수와 initialState를 인수로 받아 상태와 상태를 업데이트하는 dispatch를 반환
  const [state, dispatch] = useReducer(reducer, initialState);
  // Context.Provider에 제공되는 값으로, 상태(state)와 상태를 업데이트하는 함수(dispatch)를 포함한 객체
  const value = { state, dispatch };
  return <Context.Provider value={value}>{children}</Context.Provider>
};

export { Context, Provider };
```
*Context 초기 설정*

```jsx
import React, { useContext } from 'react';
import { Context } from '../../Context/index';
import AccountBalanceWalletIcon from '@mui/icons-material/AccountBalanceWallet';

const UserInfo = () => {
    const { state: { user }, dispatch } = useContext(Context);

    return (
        <div className={styles.walletAddress}>
            <AccountBalanceWalletIcon className={styles.walletIcon}/>
            <p className={styles.address}>
                {`${user.account.slice(0,6)}...${user.account.slice(-5)}`}
            </p>
        </div>
    )
};
```
*Context 사용 예시*  

내가 발행한 NFT를 가져오는 방식은 메인 페이지와 비슷하게 구현했다. 조금 다른 것은 컨트랙트 메소드인데, `getNftTokenList` 메소드이다. 이 메소드는 로그인한 유저의 지갑 주소를 전달하여 해당 지갑 주소로 발행한 NFT 목록만 받아올 수 있다.

```jsx
    /**
     * 사용자의 토큰을 가져오는 함수다.
     */
    const getUserToken = async () => {
        let contractAddress = process.env.REACT_APP_ERC_721_ADDRESS;
    try {
        const response = await get721Contract(contractAddress).methods.getNftTokenList(cookies.address).call();
        console.log('response', response)
        setNftList(response.map(nft => [Number(nft[0]), nft[1]]));
    } catch (error) {
        console.error(error);
    }
    }
    useEffect(() => {
        getUserToken()
    }, []);

    /** 
   * 주어진 URL을 IPFS 주소로 변환하는 함수.
   * 
   * @param {string} url 변환할 URL.
   * @returns {string | undefined} IPFS 주소로 변환된 URL입니다. URL이 주어지지 않은 경우 `undefined`를 반환.
   */
  const IpfsParser = (url) => {
    const cid = url.slice(7,url.length)
    const ipfsUrl = "https://ipfs.io/ipfs/" + cid
    return ipfsUrl
  }
    

useEffect(() => {
    const fetchData = async (url) => {
      try {
        const response = await fetch(IpfsParser(url));
        const data = await response.json();
        return Array.isArray(data) ? data : [data];
      } catch (error) {
          console.error(error);
      }
    };
  
    const fetchAllData = async () => {
      try {
        const allData = await Promise.all(NftList.map(async data => fetchData(data[1])));
        setInfoNft(prevList => [...prevList, ...allData.flat()]);
        console.log('jsonData', allData);
      } catch (error) {
          console.error(error);
      }
    };
  
    fetchAllData();
  }, [NftList]);
```
*소유한 NFT 목록을 가져오는 코드*

> Detail Page

![DetailPage](../../assets/img/codestates/detailPage.png)  
*Detail Page*

상세 페이지는 메인 페이지나 마이 페이지에서 각 NFT를 클릭하면 진입할 수 있다. 상세 페이지에서는 NFT의 정보가 출력이 되는데 NFT의 타이틀, 이미지, 가격, 설명, 카테고리, 작가의 링크 등을 볼 수 있다.
현재 구매 버튼은 구현을 해놨으나 기능은 연결하지 않은 상태이다. 이 부분까지는 시간이 부족해서 하지 못했다..ㅠ
상세 페이지에서 NFT의 정보를 가져오는 부분은 정말 많이 헤맸는데, 새벽이어서 그런건지 머리가 정말 안돌아갔다. DB가 있었으면 `id` 를 이용해 쉽게 가져올 수 있었을 텐데, 우리는 DB를 사용하지 않아 `id`를 매칭하여 가져오는 부분이 계속 해결이 되지 않았다. 그러던 중 찾은 방법이 `Link` 엘리먼트를 사용하여 데이터를 전달해주는 방법이었다. 이 방법을 보고 정말 유레카를 외치고 싶은 심정이었다.

```jsx
{infoNft.map((data, i) => {
  console.log("data", data, i)
  return (
    <div className={`${styles.imgWrap} ${styles.nftImage}`} key={i}>
      {/* {console.log(NftList[i][0])} */}
      <Link to={`/detail/${i}`} state={{ info: data }}>
        <img src={IpfsParser(data.image)} alt={`Image ${i}`}/>
      </Link>
    </div>
  )
})}
```
*메인 페이지에서 Link의 state를 사용하여 상세 페이지로 NFT 정보를 전달하는 코드*

```jsx
import { useLocation } from 'react-router-dom'

const location = useLocation();
const info = location.state.info;

<>
  <div className={styles.detailContainer}>
    <div className={styles.left}>
        <div className={styles.imageContainer}>
          <img src={IpfsParser(info.image)} alt="NFT image" className={styles.squareImage} />
        </div>
        
        
    </div>
    <div className={styles.right}>
        <div className={styles.titleContainer}>
            <h1 className={`${styles.title} ${styles.owned} ${styles.titleSize}`}>{info.name}</h1>
            <p className={`${styles.title} ${styles.owned}`}>Owned by {owned}</p>
        </div>
        

        <div className={styles.priceContainer}>
            <div>
                <span>Current price</span>
                <h1 className={styles.priceVal}>{Number(info.price)}ETH</h1>
            </div>
            <button className={styles.buyBtn}><h3>Buy now</h3></button>
        </div>

        <div className={styles.Description}>
            <h3 className={styles.DescriptionH3}>Description</h3>
            <div className={styles.DescriptionLine}></div> {/* Add a separate div for the line */}
            <p className={styles.DescriptionP}>{info.description}</p>
            <div className={styles.DescriptionLine}></div>
            <h3 className={styles.DescriptionDitails}>Details</h3>
            <div className={styles.DescriptionLine}></div>
            <div className={styles.DescriptionVal}>
                <div >
                Category
                <span className={styles.rightAlign}>{info.properties.category}</span>
                </div>
                <div>
                ExLink
                <span className={styles.rightAlign}>{info.properties.exLink}</span>
                </div>
            </div>
        </div>
        
    </div>
  </div>
</>
```
*전달 받은 NFT 정보를 사용하는 상세 페이지 코드*

React Router 라이브러리의 `Link` 컴포넌트는 `state` prop을 제공하여 라우트 간에 상태를 전달 할 수 있다. `useLocation`을 사용하여 현재 위치의 상태를 읽는다. `state` prop은 이동된 위치에만 적용된다.

### 마무리
이렇게 첫 프로젝트는 마무리가 됐다. 정말 우여곡절이 많았는데, 이번에 챗 지피티의 도움을 정말 많이 받았다. 질문이 너무 많아서 여기에 정리하기에는 내용이 너무 많아서 힘들지만 웬만한 것은 다 물어본 것 같다. 이번에 프로젝트를 하면서 팀장이라는 역할이 정말 힘들다는 것도 깨달았다. 이전에 회사를 다니면서 팀장님께 정말 많이 질문을 하면서 괴롭혔는데, 그 나날들을 반성하게 되면서 다시 한 번 팀장님들을 존경하게 됐다. 팀장님들이 맨날 본인이 맡은 일을 하기가 시간이 부족하다고 했는데 어떤 말인지 완전히 깨닫게 되는 순간들이었다. 그리고 좀 더 많은 것들을 다양하게 시도해보고 싶었는데 시간이 부족해서 그러지 못한 것도 아쉽고, 처음에 시작할 때 제대로 규칙이나 기획을 정하지 않아서 시간이 더 소요된 것 같아 그 부분도 많이 아쉽다. 짧은 시간이었지만 그럼에도 결과물을 잘 만들어주고 같이 밤새면서 열심히 노력해준 팀원분들께 정말 감사했다고 전하고 싶다.  
다음 프로젝트에서는 상태 관리 라이브러리나 CSS 라이브러리 등 좀 더 다양한 것들을 시도해 볼 생각이다.

> [Git Hub Repository](https://github.com/KimSeoYeon23/beb-09-miumiu)
 -->
