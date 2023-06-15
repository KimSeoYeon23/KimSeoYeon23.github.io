---
layout: post
title:  "가상 클래스"
date:   2023-06-15 15:30:00 +0900
categories: 
  - Dev
  - css
tag: css
comments: true
---
CSS 의사 클래스(가상 클래스)는 선택자에 추가하는 키워드로, 선택한 요소가 특별한 상태여야 만족할 수 있다.
예를 들어 `:hover`를 사용하면 포인터를 올렸을 때에만 글씨 색을 바꾸고 싶을 때 사용할 수 있다.

```css
a:hover {
	color: red;
}
```

의사 클래스를 사용하면 문서 트리 콘텐츠와 관련된 경우 뿐만 아니라 탐색기 히스톨(`:visited` 등), 콘텐츠의 상태(특정 폼 요소에 적용한`:checked` 등), 마우스의 위치(커서가 마우스 위인지 아닌지 알 수 있는 `:hover` 등)처럼 외부 인자와 관련된 경우에도 스타일을 적용할 수 있다.

- `:hover`
  - HTML 요소에 마우스 커서가 올라가 있는 동안 서택
  ```css
  a:hover {
    color: red;
  }
  ```  
- `:active`
  - HTML 요소에 마우스를 클릭하고 있는 동안 선택
  ```css
  a:active {
	  color: red;
  }
  ```  
- `:checked`
  - 선택했거나 `on` 상태인 라디오(`<input type='radio'>`), 체크박스(`<input type='checkbox'>`), 옵션(`<option>`) 요소를 나타낸다.
  ```css
  input:checked {
    margin-left: 25px;
    border: 1px solid blue;
  }
  ```  
- `:disabled`
  - 모든 비활성 요소를 나타낸다.
  - 비활성 요소란 활성(선택, 클릭, 입력 등등) 하거나 포커스를 받을 수 없는 요소를 말한다.
  ```css
  /* 모든 비활성 <input> 선택 */
  input:disabled {
    background: #ccc;
  }
  ```  
- `:first-child`
  - 형제 요소 중 제일 첫 요소를 나타낸다.
  ```css
  p:first-child {
    color: lime;
  }
  ```  
- `:focus`
  - 양식의 입력 칸 등 포커스를 받은 요소
  - 보통 사용자가 요소를 클릭 또는 탭하거나, 키보드 `Tab`키로 선택했을 때 발동한다.
  ```css
  /* Selects any <input> when focused */
  input:focus {
    color: red;
  }
  ```  
- `:last-child`
  - 형제 요소 중 제일 마지막 요소를 나타낸다.
  ```css
  li:last-child {
    color: red;
  }
  ```  
- `:link`
  - 아직 방문하지 않은 요소를 나타낸다.
  - `href` 속성을 가진, `<a>`, `<area>`, `<link>` 중 방문하지 않은 모든 요소를 선택한다.
  ```css
  /* 아직 방문하지 않은 <a> 요소를 선택 */
  a:link {
    color: red;
  }
  ```  
- `:nth-child`
  - 형제 사이에서의 순서에 따라 요소를 선택한다.
  ```css
  /* 목록의 두 번째 <li> 선택 */
  li:nth-child(2) {
    color: lime;
  }

  /* 임의의 그룹에서 네 번째에 위치하는 모든 요소 선택 */
  :nth-child(4n) {
    color: lime;
  }
  ```  
- `:visited`
  - 사용자가 방문한 적이 있는 링크를 나타낸다.
  - `:visited`가 바꿀 수 있는 스타일은 개인정보 보호를 위해 매우 제한적이다.
  ```css
  /* 방문한 적이 있는 <a> 선택 */
  a:visited {
    color: green;
  }
  ```  

더 많은 CSS 의사 클래스에 대해서는 [MDN](https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes) 사이트에서 확인할 수 있다.