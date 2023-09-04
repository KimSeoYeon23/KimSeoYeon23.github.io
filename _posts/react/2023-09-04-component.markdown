---
layout: post
title:  "Component"
date:   2023-09-04 22:40:00 +0900
categories: 
  - Dev
  - react
tag: react
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## Component

### 하나의 기능 구현을 위한 여러 종류의 코드 묶음, UI를 구성하는 필수 요소

리액트를 이용하면, 각자 독립적인 기능을 가지며 UI의 한 부분을 담당하기도 하는 이러한 컴포넌트를 여러 개 만들고 조합하여 애플리케이션을 만들 수 있다.

![Application](../../assets/img/react/component.png){:.centered}

모든 리액트 애플리케이션은 최소 한 개의 컴포넌트를 가지고 있으며, 이 컴포넌트는 애플리케이션 내부적으로 근원(root)이 되는 역할을 한다. 이 최상위 컴포넌트는 근원의 역할을 하므로 다른 자식 컴포넌트를 가질 수 있다. 이 계층적 구조(hierarchy)를 트리 구조로 형상화 할 수 있다.

![트리구조](../../assets/img/react/component_2.png){:.centered}

만약 하나의 페이지를 리액트로 만든다고 보면 아래의 그림처럼 여러 개의 컴포넌트가 모여서 하나의 페이지를 이루게 된다.

![컴포넌트 예시](../../assets/img/react/component_4.png){:.centered}

이 인스타그램 페이지를 보면 여러 개의 컴포넌트로 이루어져 있다. 검색, 프로필, 스토리, 포스트 컴포넌트 등으로 구성되어 있는데, 이렇게 컴포넌트가 여러 개로 나누어져 있기 때문에 하나의 컴포넌트를 여러 곳에서 사용할 수 있다.  
또한 여러 명이 각자 맡은 컴포넌트를 동시에 수정할 수도 있다.

### 리액트 컴포넌트 종류

![컴포넌트 종류](../../assets/img/react/component_3.png){:.centered}

- 클래스형 컴포넌트(Class Components)
- 함수형 컴포넌트(Functional Components)

원래 리액트로 개발할 때는 클래스 컴포넌트를 이용해서 많이 개발을 했지만, 리액트에서 리액트 Hooks라는 것을 발표한 이후부터는 함수형 컴포넌트를 이용해서 개발을 많이 한다.