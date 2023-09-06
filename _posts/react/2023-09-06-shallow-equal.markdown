---
layout: post
title:  "얕은 비교와 깊은 비교"
date:   2023-09-06 20:40:00 +0900
categories: 
  - Dev
  - react
tag: react
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 얕은 비교(Shallow Compare) 란?

숫자, 문자열 등 원시 자료형은 값을 비교한다.  
배열, 객체 등 ㅊ마조 자료형은 값 혹은 속성을 비교하지 않고, **참조되는 위치**를 비교한다.

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };

console.log(obj1 === obj2); // false
```
*값 대신 참조되는 위치를 비교하기 때문에 `false`가 나온다.*

## 깊은 비교란?

얕은 비교와 달리 깊은 비교는 **객체의 경우에도 값**으로 비교한다.  

깊은 비교 방법은 아래와 같다.

1. Object depth가 깊지 않은 경우: `JSON.stringify()` 사용
2. Object depth가 깊은 경우: `lodash` 라이브러리의 `isEqual()` 사용

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };

console.log(JSON.stringify(obj1) === JSON.stringify(obj2)); // true
```

### 얕은 비교를 사용할 때

- `React.memo()`에서 `props`를 비교할 때
- 리액트 컴포넌트가 리 렌더링을 하기 전
  - `state` 변경이 있을 때
  - 부모 컴포넌트가 렌더링 될 때

> 리액트가 리 렌더링이 되는 경우
> `state` 변경이 있을 때
> 부모 컴포넌트가 렌더링 될 때
> 새로운 `props`이 들어올 때
> `shouldComponentUpdate`에서 `true`가 반환될 때