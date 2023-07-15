---
layout: post
title:  "CodeStates BEB 첫 번째 프로젝트 회고"
date:   2023-06-30 15:50:00 +0900
categories: 
  - Dev
  - codestates
tag: codestates
comments: true
---

![OpenSea](../../assets/img/codestates/opensea.png)

### 프로젝트 기간 : 2023.06.23 ~ 2023.06.30

### CodeStates에서의 첫 프로젝트

**프로젝트 시작하기에 앞서**  

현재 참여 중인 코드스테이츠 부트캠프에서 첫 번째 프로젝트로 OpenSea 클론 코딩을 하게 되었다. 프로젝트의 기한은 총 6일 이었다. 6일이라는 시간도 짧은데 클론 코딩이라지만 OpenSea라니 조금은 막막한 기분이 들었다. 필수 기능을 전부 구현해야 하는 줄 알고 정말 이게 가능한가 싶던 차였는데 코드스테이츠의 담임 선생님 같은 역할이신 은성님께서 "첫 프로젝트이니 보통 완성도가 높지는 않다." 라고 말씀을 해주셔서 그나마 좀 부담감이 덜 했던 것 같다. 

### 포지션
첫 번째 프로젝트 팀원은 여자 4명이서 팀이 됐다. 첫 프로젝트이다 보니 은성님께서 편하게 진행할 수 있도록 팀원을 배정을 해주셨다. 첫 날, 각자 맡고 싶은 포지션을 정하는데 다행히 겹치는 포지션이 없이 프론트엔드 2명, 백엔드 2명으로 잘 정해졌다. 그 중 나는 원래 했었고, 하고 싶었던 프론트엔드 포지션을 맡게 되었다. 프로젝트의 최소 목표치가 다행히 높지는 않고, UR Class에 정해져 있어서 금방 감을 잡을 수 있었다.

### 구현 목표
**Bare Minium**
- Header
  - 웹 페이지 로고
  - NFT 검색 버튼
  - 마켓, NFT 민팅, 마이페이지 내비게이션
  - 지갑 연결 버튼
- Footer
  - 팀 정보 및 깃헙 페이지 등 기본적인 정보
- 메인 페이지 (랜딩 페이지)
  - NFT 리스트
- 테마별 NFT 리스트 페이지
  - 탭 기능을 활용하여 테마별 NFT 리스트 로딩
  - NFT 별 상세 페이지
- NFT 거래 페이지
  - NFT 상세 내용 정보 (이미지, 가격, 상세 설명 등)
  - 구입 버튼
- NFT 민팅 페이지
  - 텍스트 에디터 라이브러리를 사용하거나, 기본 폼으로 제작
  - 제목, 내용 칸 / 작성 버튼
  - 사진 삽입 칸
- 마이 페이지
  - 유저의 기본 정보 (지갑 주소, 이름 등등)
  - 보유하고 있는 NFT 리스트
  - 발행한 NFT 리스트
  - 지갑 연결 해제 가능 버튼
- (Optional) Not Found
  - 사용자가 요청을 잘못 보냈을 때 해당 페이지를 로드
- (Optional) Spinner
  - 로딩이 길어졌을 때 흰색 화면 대신 해당 페이지를 로드

일단은 위의 기능 중 필수적인 기능들을 구현하는 데에 초점을 맞췄다. 해당 기능들의 구현이 완료되고 시간이 남으면 부가적으로 기능을 추가하기로 팀원들과 합의 했다.

### 플로우 차트 & 화면 흐름도
![FlowChart](../../assets/img/codestates/flowchart.png){:.centered}
*플로우 차트*  

![화면흐름도](../../assets/img/codestates/display.png){:.centered}
*화면 흐름도*

본격적으로 코드를 작성하기에 앞서 우선 플로우 차트를 만들었다. 와이어 프레임은 오픈씨 홈페이지 자체를 와이어 프레임 삼아서 따로 만들지는 않았다.

### 기술 스택
**Front-end**  
<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26.svg?style=for-the-badge&logo=HTML5&logoColor=white"/>
<img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=CSS3&logoColor=white"/>
<img alt="Javascript" src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=for-the-badge&logo=JavaScript&logoColor=white"/>
<img alt="React" src="https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=white"/>
<img alt="MUI" src="https://img.shields.io/badge/MUI-007FFF.svg?style=for-the-badge&logo=MUI&logoColor=white"/>
<img alt="Web3.js" src="https://img.shields.io/badge/Web3.js-F16822.svg?style=for-the-badge&logo=Web3.js&logoColor=white"/>

**Back-end**  
<img alt="Solidity" src="https://img.shields.io/badge/Solidity-363636.svg?style=for-the-badge&logo=Solidity&logoColor=white"/>
<img alt="Node.js" src="https://img.shields.io/badge/Node.js-339933.svg?style=for-the-badge&logo=Node.js&logoColor=white"/>
<img alt="Express" src="https://img.shields.io/badge/Express-000000.svg?style=for-the-badge&logo=Express&logoColor=white"/>
<img alt="Ethers.js" src="https://img.shields.io/badge/Ethers.js-3C3C3D.svg?style=for-the-badge&logo=Ethereum&logoColor=white"/>
<img alt="IPFS" src="https://img.shields.io/badge/IPFS-65C2CB.svg?style=for-the-badge&logo=IPFS&logoColor=white"/>

**Etc**  
<img alt="npm" src="https://img.shields.io/badge/npm-CB3837.svg?style=for-the-badge&logo=npm&logoColor=white"/>
<img alt=".ENV" src="https://img.shields.io/badge/.ENV-ECD53F.svg?style=for-the-badge&logo=.ENV&logoColor=white"/>
<img alt="Discord" src="https://img.shields.io/badge/Discord-5865F2.svg?style=for-the-badge&logo=Discord&logoColor=white"/>
<img alt="Ethereum" src="https://img.shields.io/badge/Ethereum-3C3C3D.svg?style=for-the-badge&logo=Ethereum&logoColor=white"/>
<img alt="MetaMask" src="https://img.shields.io/badge/MetaMask-F16822.svg?style=for-the-badge&logo=MetaMask&logoColor=white"/>
<img alt="Sepolia" src="https://img.shields.io/badge/Sepolia-9558B2.svg?style=for-the-badge&logo=Sepolia&logoColor=white"/>

CSS 프레임워크는 MUI(Meterial-UI)를 사용했다. MUI는 리액트 개발에서 쉽게 사용할 수 있는 UI Framework이며, 높은 수준의 UI를 빠르고 효율적으로 개발할 수 있는 UI 도구이다. 또한 구글의 Meterial Design UI 가이드 라인을 바탕으로 하며, UI 개발에 필요한 수많은 컴포넌트와 디자인 템플릿을 제공한다. 원래는 Styled-Components를 사용하려 했으나 MUI가 리액트와 높은 호환성과 높은 수준의 퀄리티를 제공하기 때문에 많이 사용한다고 하여 사용해 보기로 했다. 

### 구현
**Main Page**
> Header

![MainPage](../../assets/img/codestates/mainPage.png){:.centered}
*Main Page*  
결론을 먼저 말하자면 Main Page는 이렇게 구현이 완료 되었다. Header에는 로고와 검색 할 수 있는 input, 지갑 연결 버튼, 프로필로 이동할 수 있는 버튼 등이 있다. OpenC 로고를 클릭하면 메인 페이지로 이동할 수 있다. 프로젝트 시간이 부족하여 검색 기능은 구현을 하지 못했다.  
![지갑 연결 버튼](../../assets/img/codestates/connectWallet.png){:.centered}
*지갑 연결 버튼*  
지갑 연결은 Connect Wallet 버튼을 누르면 연결이 되며  
![지갑 연결 완료](../../assets/img/codestates/wallet.png){:.centered}
*지갑 연결 완료*
지갑이 연결이 되면 연결된 지갑의 주소와 소유하고 있는 ETH 잔액을 확인할 수 있다.  
![메뉴](../../assets/img/codestates/menu.png){:.centered}
*메뉴 hover*
오른쪽의 프로필 이미지에 마우스를 hover하게 되면 이미지와 같이 마이 페이지와 민팅 페이지로 이동할 수 있는 메뉴가 나온다. 지갑 연결 해제, 즉 로그아웃은 헤더에서 구현을 했다.
마이페이지와 민팅 페이지는 지갑 연결, 즉 로그인을 해야 이동할 수 있도록 구현을 했다.  
![경고창](../../assets/img/codestates/alert.png){:.centered}
*로그인을 하지 않은 상태로 마이 페이지나 민팅 페이지 클릭 시 뜨는 경고창*

```jsx
/* 유저 account fetching */
  const fetchAccountInfo = useCallback(async () => {
    try {
      let userAddr = await getUserAccount();
      let userBal = await getUserBalance(userAddr);
      let userBalance = Number(fromWei(userBal)).toFixed(4);

      dispatch({ type: SET_ACCOUNT, payload: userAddr });
      dispatch({ type: SET_BALANCE, payload: userBalance });

      setLoginCookie(userAddr);
    } catch (e) {
      console.log(e);
    }
  }, []);

  useEffect(() => {
    fetchAccountInfo();
  }, [fetchAccountInfo]);
  
  const getSigning = useCallback(() => {
    if (user.account) { // Check if user.account exists
      localStorage.setItem('Sign', [
        `Welcome to OpenC! Click \"Sign\" to sign in. No password needed! I accept the MetaWis Terms of Service: Wallet address:${user.account.toLowerCase()}`,
      ]);
    }
  }, [user.account]); // Depend on user.account
  
  useEffect(() => {
    getSigning(); // Call getSigning when user.account changes
  }, [getSigning]);

  // 메타마스크 연결
  const LoginWallet = async () => {

    // 유저 브라우저 확인
    let agent = navigator.userAgent.toLowerCase();

    try {
      await window.ethereum.request({ method: 'eth_requestAccounts' });
    } catch (error) {
      console.log(error);
      if (!window.ethereum) {
        // 메타마스크 설치가 안되어 있을 경우 설치 페이지로 이동
        if (agent.indexOf('chrome') != -1 || agent.indexOf('msie') != -1) {         // 크롬일 경우
          window.open(`${process.env.REACT_APP_INSTALL_META_CHROME}`, '_blank');
        } else if (agent.indexOf('firefox') != -1) {                                // firefox일 경우
          window.open(`${process.env.REACT_APP_INSTALL_META_FIREFOX}`, '_blank');
        }
      }
    }

    fetchAccountInfo();
    getSigning();
  };
```
*메타마스크 연결 코드*  

```jsx
// 메타마스크 연결 해제
  const Logout = () => {
    setOpen(false); 
    removeLoginCookie();
    navigate('/')
    dispatch({ type: SET_LOGOUT });   // Context 상태 초기화
  };
```
*메타마스크 연결 해제 코드*

> 슬라이드 구현

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

