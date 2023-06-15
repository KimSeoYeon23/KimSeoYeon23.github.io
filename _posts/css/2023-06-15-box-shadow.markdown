---
layout: post
title:  "box-shadow 속성"
date:   2023-06-15 16:25:00 +0900
categories: 
  - Dev
  - css
tag: css
comments: true
---

`box-shadow` 속성은 요소의 테두리를 감싼 그림자 효과를 추가한다. 쉼표로 구문해서 여러 그림자 효과를 입힐 수 있다.
박스 그림자는 요소에서의 수평수직 거리(오프셋), 흐릿함과 확산 정도, 색상으로 이루어진다.  

- `inset`
  - 값을 지정하지 않으면(기본값) 요소가 공중에 떠있는 것처럼 밖에 드리우는 그림자가 된다.
  - `inset` 키워드가 존재하면 요소가 움풀 들어간 것처럼 그림자가 요소의 테두리 안, 배경색 위, 내부 콘텐츠 밑에 그려진다.  

- `<offset-x>`, `<offset-y>`
  - 그림자 위치를 설정한다.
  - `<offset-x>`는 수평 거리를 의미하며, 음수 값은 그림자를 요소의 왼쪽에 표시한다.
  - `<offset-y>`는 수직 거리를 의미하며, 음수 값은 그림자를 요소의 위쪽에 표시한다.
  - 두 값이 모두 `0`이면 그림자가 요소 바로 뒤쪽에 위치하며, `<blur-radius>` 또는 `<spread-radius>`가 존재하면 흐려지는 효과를 볼 수 있다.

- `<blur-radius>`
  - 크면 클 수록 그림자 테두리가 흐려지므로 크기는 더 커지고 색은 더 밝아진다.
  - 음수 값은 사용할 수 없다.
  - 값을 설정하지 않으면 `0`이 되어 테두리가 선명해진다.

- `<spread-radius>`
  - 양수 값은 그림자가 더 커지고 확산하며, 음수 값은 그림자가 줄어든다.
  - 기본값은 `0`(그림자와 요소 크기 동일)이다.

- `<color>`
  - 기본값은 브라우저에 따라 다르다. 보통 `color` 속성의 값을 사용한다.
  - Safari는 투명한 그림자가 기본값이다.

```css
/* offset-x | offset-y | color */
box-shadow: 60px -16px teal;

/* offset-x | offset-y | blur-radius | color */
box-shadow: 10px 5px 5px black;

/* offset-x | offset-y | blur-radius | spread-radius | color */
box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);

/* inset | offset-x | offset-y | color */
box-shadow: inset 5em 1em gold;

/* Any number of shadows, separated by commas */
box-shadow: 3px 3px red, -1em 0 0.4em olive;

/* Global keywords */
box-shadow: inherit;
box-shadow: initial;
box-shadow: unset;
```