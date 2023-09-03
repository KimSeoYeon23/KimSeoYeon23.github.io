---
layout: post
title:  "이벤트 버블링과 캡쳐링"
date:   2023-09-03 20:20:00 +0900
categories: 
  - Dev
  - javascript
tag: javascript
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 버블링과 캡쳐링

### 버블링

이벤트 버블링이란 한 요소에 이벤트가 발생하면 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러가 최상위 요소를 만날 때까지 반복되면서 핸들러가 동작하는 현상을 말한다.

`<div class="DIV3">DIV3</div>`를 클릭하면 할당되어 있는 이벤트가 발생하고 다음에는 바깥의 `div` 태그에 할당된 이벤트가 발생하고 `document` 객체를 만날 때까지 이벤트가 전파된다.

![이벤트 버블링](../../assets/img/javascript/bubbling.png){:.centered}
*이벤트 버블링*

**버블링을 막는 방법**

- `event.stopPropagation()`
  - 이벤트가 상위 엘리먼트에 전달되지 않게 막아준다.
  - 이벤트 버블링을 막아준다.

```js
  target.addEventListener('click', function(e) {
    e.stopPropagation();
  });
```

### 캡쳐링

버블링과 반대로 최상위 태그에서 해당 태그를 찾아 내려간다.  

`addEventListener`의 옵션 객체에 `{ capture: true }` 또는 `true`를 설정해주면 캡쳐링을 구현할 수 있다.

![이벤트 캡쳐링](../../assets/img/javascript/capturing.png){:.centered}
*이벤트 캡쳐링*

```js
  target.addEventListener('click', function(e) {}, true);
  target.addEventListener('click', function(e) {}, { capture: true });
```