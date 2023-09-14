---
layout: post
title:  "시작하기"
date:   2023-09-14 23:45:00 +0900
categories: 
  - Dev
  - vue
tag: vue
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## Vue 프로젝트 설치

```bash
npm create vue@latest
```

위의 명령어를 실행하면 옵션을 선택하는 프롬프트가 뜬다.

```bash
✔ Project name: … <your-project-name>
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit testing? … No / Yes
✔ Add an End-to-End Testing Solution? … No / Cypress / Playwright
✔ Add ESLint for code quality? … No / Yes
✔ Add Prettier for code formatting? … No / Yes

Scaffolding project in ./<your-project-name>...
Done.
```

프로젝트 이름을 설정하고, 여러가지 옵션을 설정할 수 있는데 일단은 전부 No로 선택했다.

### Vue 실행

```bash
cd <your-project-name>
npm install
npm run dev
```

![첫 실행화면](../../assets/img/vue/vue_start.png){:.centered}

<http://localhost:5173> 으로 접속하면 정상적으로 화면이 렌더링 되는 것을 확인할 수 있다.

## Vue 컴포넌트

### 싱글 파일 컴포넌트

Vue 싱글 파일 컴포넌트(Single-File Components: SFC, 일명 `*.vue` 파일)는 컴포넌트의 템플릿, 로직 및 스타일을 하나의 파일로 묶어낸 특수한 파일 형식이다.

```jsx
<script setup>
import { ref } from 'vue'
const greeting = ref('Hello World!')
</script>

<template>
  <p class="greeting">{{ greeting }}</p>
</template>

<style>
.greeting {
  color: red;
  font-weight: bold;
}
</style>
```

Vue SFC는 HTML, CSS 및 JavaScript 이 3개를 하나로 자연스럽게 합친 것이다. `<template>`, `<script>` 및 `<style>` 블록은 하나의 파일에서 컴포넌트의 뷰, 로직 및 스타일을 캡슐화하고 배치한다.

SFC 사용을 위해서는 빌드 방식을 따라야 하지만 다음과 같은 많은 이점이 있다.

- 친숙한 HTML, CSS 및 JavaScript 문법을 사용하여 모듈화된 컴포넌트 작성
- [본질적으로 사용 목적에 따라 구성](https://ko.vuejs.org/guide/scaling-up/sfc.html#why-sfc)
- [컴포넌트 범위 CSS](https://ko.vuejs.org/api/sfc-css-features.html)
- [컴포지션 API로 작업할 때 더욱 인체공학적인 문법](https://ko.vuejs.org/api/sfc-script-setup.html)
- 템플릿과 스크립트를 교차 분석하여 컴파일 시간을 더욱 더 최적화
- 템플릿 표현식을 [지원하는 IDE](https://ko.vuejs.org/guide/scaling-up/tooling.html#ide-support)의 자동 완성 및 유형 검사
- 즉시 사용 가능한 핫 모듈 교체(Hot-Module Replacement: HMR) 지원

SFC는 Vue를 프레임워크로 정의하며, 다음과 같이 Vue를 사용하는 데 권장되는 접근 방식이다.

- 싱글 페이지 앱(SIngle Page Application: SPA)
- 정적 사이트 생성(Static-Site Generator: SSG)
- 더 나은 개발 경험(DX)을 위해 프론트엔드 개발 방식에 합리적으로 빌드 방식 도입

### 작동 방식

Vue SFC는 프레임워크별 파일 형식이며, `@vue/complier-sfc`를 통해 표준 JavaScript와 CSS로 미리 컴파일 되어있어야 한다. 컴파일 된 SFC는 표준 JavaScript(ES) 모듈이다. 즉, 적절한 빌드 설정으로 SFC를 모듈처럼 가져올 수 있다.

```jsx
import MyComponent from './MyComponent.vue'

export default {
  components: {
    MyComponent
  }
}
```

SFC 내부의 `<style>` 태그는 일반적으로 핫 업데이트를 지원하기 위해 개발 중에는 기본 `<style>` 태그로 삽입된다. 프로덕션을 위해 단일 CSS 파일로 추출 및 병합할 수 있다.

### 컴포넌트 사용하기

자식 컴포넌트를 사용하려면 부모 컴포넌트에서 가져와야 한다. 파일 안에 `ButtonCounter.vue`라는 카운터 컴포넌트를 배치했다고 가정하면, 해당 컴포넌트 파일의 기본 내보내기가 노출된다.

```jsx
<script setup>
import ButtonCounter from './ButtonCounter.vue'
</script>

<template>
  <h1>아래에 자식 컴포넌트가 있습니다.</h1>
  <ButtonCounter />
</template>
```

`<script setup>`을 사용하면 가져온 컴포넌트를 템플릿에서 자동으로 사용할 수 있다.

컴포넌트를 전역으로 등록하면 가져오기(import) 없이 지정된 앱의 모든 곳에서 컴포넌트를 사용할 수 있다.

컴포넌트는 원하는 만큼 재사용할 수 있다.

### 컴포넌트 등록

**전역 등록**

`app.component()` 메서드를 사용하여 현재 Vue 앱에서 컴포넌트를 전역으로 사용할 수 있도록 할 수 있다.

```jsx
import { createApp } from 'vue'

const app = createApp({})

app.component(
  // 등록될 이름
  'MyComponent',
  // 구현체
  {
    /* ... */
  }
)
```

SFC를 사용하는 경우, 가져온 `.vue` 파일을 등록한다.

```jsx
import MyComponent from './App.vue'

app.component('MyComponent', MyComponent)
```

`app.component()` 메서드는 다음과 같이 연결할 수 있다.

```jsx
app
  .component('ComponentA', ComponentA)
  .component('ComponentB', ComponentB)
  .component('ComponentC', ComponentC)
```

전역으로 등록된 컴포넌트는 앱 내의 모든 컴포넌트 템플릿에서 사용할 수 있다.

```jsx
<!-- 이것은 앱 내부의 모든 컴포넌트 내에서 작동합니다. -->
<ComponentA/>
<ComponentB/>
<ComponentC/>
```

이는 모든 자식 컴포넌트에도 적용된다. 즉, 이 세 컴포넌트 모두 서로의 내부에서도 사용될 수 있다.

**로컬 등록**

편리하지만 전역 등록에는 몇 가지 단점이 있다.

1. 전역 등록은 빌드 시스템이 사용하지 않는 컴포넌트를 제거하는 것(일명 “tree-shaking”)을 방지한다. 컴포넌트를 전역적으로 등록했지만 결국 앱의 어느곳에서도 사용하지 않으면 최종 번들에 계속 포함된다.
2. 전역 등록은 대규모 앱에서 의존 관계를 덜 명확하게 만든다. 자식 컴포넌트를 사용하는 부모 컴포넌트에서 자식 컴포넌트의 구현을 찾기가 어렵다. 이것은 너무 많은 전역 변수를 사용하는 것과 유사하므로 장기적인 유지 관리 측면에 영향을 줄 수 있다.

로컬 등록은 등록된 컴포넌트의 가용성 범위를 현재 컴포넌트로만 제한한다. 의존 관계를 더 명시적으로 만들고, 트리-쉐이킹에 더 친숙하다.

SFC를 사용할 때, `<script setup>` 로 가져온 컴포넌트는 등록절차 없이 로컬로 사용할 수 있다.

```jsx
<script setup>
import ComponentA from './ComponentA.vue'
</script>

<template>
  <ComponentA />
</template>
```

`<script setup>`이 아닌 경우 `components` 옵션을 사용해야 한다.

```jsx
import ComponentA from './ComponentA.js'

export default {
  components: {
    ComponentA
  },
  setup() {
    // ...
  }
}
```

`components` 객체의 각 속성에 대한 키는 컴포넌트의 이름으로 등록되고, 값은 컴포넌트의 구현이 포함된다다. 위의 예는 ES2015 속성 약칭을 사용하고 있으며 다음과 동일하다:

```jsx
export default {
  components: {
    ComponentA: ComponentA
  }
  // ...
}
```

**로컬로 등록된 컴포넌트는 자식 컴포넌트에서 사용할 수 없다**. 이 경우 `ComponentA`는 현재 컴포넌트에서만 사용할 수 있으며, 자식 컴포넌트에서 사용할 수 없다.

> 출처: [Vue 공식 문서](https://ko.vuejs.org/guide/components/registration.html#prop-passing-details)
>