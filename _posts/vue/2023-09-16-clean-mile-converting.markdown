---
layout: post
title:  "Clean Mile Converting - 1"
date:   2023-09-14 23:45:00 +0900
categories: 
  - Dev
  - vue
tag: vue
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## Clean Mile Converting

코드스테이츠 부트캠프에서 자체 제작한 프로젝트 **"Clean Mile"**을 **Vue.js**로 컨버팅 해볼 것이다.

컨버팅을 결심한 이유는 요즘 취업 준비로 채용 공고에서 기술 스택으로 **Vue.js**를 생각보다 많이 사용하는 것을 봤다.
**React.js**와 **Vue.js**의 차이점을 문서로만이 아닌 직접 사용해보면서 느껴보고 싶어 결정했다.

## 기술 스택

우선 기존의 프로젝트의 기술스택은 이렇다.

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

**Vue.js**에는 어떤 라이브러리들이 있는지 아직 파악이 되지 않아 정확히 기술하기는 어렵지만, 컨버팅 해보면서 추가할 예정이다.

<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26.svg?style=for-the-badge&logo=HTML5&logoColor=white"/>
<img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=CSS3&logoColor=white"/>
<img alt="Javascript" src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=for-the-badge&logo=JavaScript&logoColor=white"/>
<img alt="Vue.js" src="https://img.shields.io/badge/Vue.js-4FC08D.svg?style=for-the-badge&logo=Vue.js&logoColor=white"/>
<img alt="Font Awesome" src="https://img.shields.io/badge/FontAwesome-528DD7.svg?style=for-the-badge&logo=FontAwesome&logoColor=white"/>
<img alt="Pinia" src="https://img.shields.io/badge/Pinia-F0B90B.svg?style=for-the-badge&logo=Pinia&logoColor=white"/>
<img alt="Vue Query" src="https://img.shields.io/badge/vuequery-FF4154.svg?style=for-the-badge&logo=vuequery&logoColor=white"/>
<img alt="vuei18n" src="https://img.shields.io/badge/vuei18n-26A69A.svg?style=for-the-badge&logo=vuei18n&logoColor=white"/>
<img alt="Axios" src="https://img.shields.io/badge/Axios-5A29E4.svg?style=for-the-badge&logo=Axios&logoColor=white"/>
<img alt="web3.js" src="https://img.shields.io/badge/web3.js-F16822.svg?style=for-the-badge&logo=web3.js&logoColor=white"/>
<img alt="three.js" src="https://img.shields.io/badge/three.js-000000.svg?style=for-the-badge&logo=three.js&logoColor=white"/>
<img alt="SweetAlert2" src="https://img.shields.io/badge/SweetAlert2-FF6666.svg?style=for-the-badge&logo=SweetAlert2&logoColor=white"/>

리액트에서는 **react-icons** 라이브러리를 사용할 수 없어 `**Font Awesome**으로 대체했고, 상태관리 라이브러리는 **Vue.js** 공식 상태관리 라이브러리인 **Pinia**를 사용할 예정이다. 이외에도 **React Query**나 다국어도 **Vue.js**에 맞는 라이브러리로 사용할 예정이다.

---

## Header 

```js
<template>
  <header class="header">
    <div class="logo-wrap">
      <img src="../assets/images/clean_mile_logo_2.png" alt="로고 이미지" />
    </div>
    <div class="category-wrap">
      <nav>
        <ul class="category">
          <li>Info</li>
          <li>Notice</li>
          <li>Events</li>
          <li>Community</li>
        </ul>
      </nav>
      <div class="btn-wrap">
        <button>로그인</button>
        <button>회원가입</button>
      </div>
    </div>
  </header>
</template>

<style lang="scss">
@import '../assets/variables.scss';

.header {
  width: 100%;
  height: 5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 3rem;
  background-color: white;
  border-bottom: 1px solid rgb(107 114 128 / 0.2);

  .logo-wrap {
    width: 20%;
    display: flex;
    align-items: center;
    img {
      width: 50%;
    }
  }

  .category-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 2.5rem;

    .category {
      display: flex;
      gap: 3.5rem;
      list-style: none;

      li {
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.2s;

        &:hover {
          color: $main-green;
        }
      }
    }
  }
}

.btn-wrap {
  display: flex;
  gap: 1rem;

  button {
    &:first-child {
      color: $main-yellow;
      background-color: transparent;
      border: none;
      cursor: pointer;
      transition: all 0.3s;
      padding: 0.5rem 1rem;

      &:hover {
        color: black;
        background-color: $main-yellow;
        border-radius: 0.5rem;
      }
    }

    &:last-child {
      color: rgb(107 114 128);
      background-color: $main-green;
      border: none;
      border-radius: 0.5rem;
      transition: all 0.3s;
      cursor: pointer;
      padding: 0.5rem 1rem;

      &:hover {
        background-color: rgb(22 163 74);
        color: white;
      }
    }
  }
}

</style>
```

*Header.js*

우선 `Header`에 아직 기능은 추가하지 않은 상태이고, 퍼블리싱만 적용한 상태이다.

프로젝트를 제작하면서 정한 기본적인 4가지 컬러가 있는데, 이 컬러를 여러 군데에서 공통적으로 사용하기 위해 `SCSS`를 설치했다. 

```bash
npm install sass
```

*sass 설치*

`variables.scss` 파일을 하나 만들어 공통으로 사용할 컬러 변수를 생성해준 뒤, 사용할 파일에서 `import` 해오면 간편하게 사용할 수 있다.

## Footer

```js
<template>
  <footer>
    <div>
      <a href="https://github.com/codestates-beb/beb-09-clean-mile" target="_blank">
        <font-awesome-icon :icon="['fab', 'github']" size="2xl"/>
      </a>
      <a href="javascript:void(0);">
        <font-awesome-icon :icon="['fab', 'instagram']" size="2xl"/>
      </a>
      <a href="javascript:void(0);">
        <font-awesome-icon icon="envelope" size="2xl"/>
      </a>
      <a href="javascript:void(0);">
        <font-awesome-icon :icon="['fab', 'discord']" size="2xl"/>
      </a>
    </div>
    <div>
      <p>Copyright &copy; 2023 Clean Mile</p>
    </div>
  </footer>

</template>

<style lang="scss">
@import '../assets/variables.scss';

footer {
  width: 100%;
  height: 14rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 3rem;
  background-color: rgb(21 128 61);

  div {
    &:first-child {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 3rem;

      a {
        color: white;
        border: 1px solid white;
        border-radius: 0.75rem;
        padding: 0.75rem;
        cursor: pointer;
      }
    }

    &:last-child {
      p {
        color: white;
        font-weight: 500;
      }
    }
  }
}
</style>
```

*Footer.js*

`Footer`에는 깃허브, 디스코드, 이메일, 인스타그램 등 아이콘을 사용하기 위해 `Font Awesome`을 사용했다. `Font Awesome`을 사용하기 위해서 기본적으로 필요한 라이브러리를 설치했다.

```bash
npm install @fortawesome/fontawesome-svg-core
npm install @fortawesome/free-solid-svg-icons
npm install @fortawesome/vue-fontawesome
npm install @fortawesome/free-brands-svg-icons
```

*FontAwesome 및 Vue.js 용 FontAwesome 라이브러리 설치*

`FontAwesome` 아이콘을 사용하기 위해 기본적인 설정을 해야 한다.

```js
import './assets/main.css';
import { library } from '@fortawesome/fontawesome-svg-core';
import { faEnvelope } from '@fortawesome/free-solid-svg-icons';
import { faGithub, faDiscord, faInstagram } from '@fortawesome/free-brands-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

import { createApp } from 'vue';
import App from './App.vue';

library.add(faGithub, faDiscord, faInstagram, faEnvelope);

const app = createApp(App);

app.component('font-awesome-icon', FontAwesomeIcon);

app.mount('#app');
```

*main.js*

1. `Font Awesome` 라이브러리에서 사용할 아이콘들을 `library`에 추가한다.
2. 그 후, `FontAwesomeIcon ` 컴포넌트를 전역 컴포넌트로 등록한다.

이렇게 설정하고 나면, 어떤 컴포넌트에서든 `<font-awesome-icon :icon="['fab', 'github']" size="2xl"/>`와 같은 방식으로 `Font Awesome` 아이콘을 사용할 수 있다.

GitHub과 Discord 아이콘을 추가하려면 `@fortawesome/free-brands-svg-icons` 패키지를 설치해야 한다. 이 패키지에는 다양한 브랜드의 로고 아이콘들이 포함되어 있다.