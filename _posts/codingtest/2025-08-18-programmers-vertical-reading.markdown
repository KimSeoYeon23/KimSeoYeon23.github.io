---
layout: post
title:  "세로 읽기"
date:   2025-08-18 17:37:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 세로 읽기

### 문제

문자열 `my_string`과 두 정수 `m`, `c`가 주어집니다. `my_string`을 한 줄에 `m` 글자씩 가로로 적었을 때 왼쪽부터 세로로 `c`번째 열에 적힌 글자들을 문자열로 return 하는 solution 함수를 작성해 주세요.

## 제한 사항

- `my_string`은 영소문자로 이루어져 있습니다.
- 1 ≤ `m` ≤ `my_string`의 길이 ≤ 1,000
- `m`은 `my_string` 길이의 약수로만 주어집니다.
- 1 ≤ `c` ≤ `m`


### 예시

입출력 예 #1

- 예제 1번의 `my_string`을 한 줄에 4 글자씩 쓰면 다음의 표와 같습니다.

|1열|	2열|	3열|	4열|
|---|---|---|---|
|i|	h|	r|	h|
|b|	a|	k|	r|
|f|	p|	n|	d|
|o|	p|	l|	j|
|h|	y|	g|	c|

2열에 적힌 글자를 세로로 읽으면 happy이므로 "happy"를 return 합니다.

입출력 예 #2

- 예제 2번의 `my_string`은 `m`이 1이므로 세로로 "programmers"를 적는 것과 같고 따라서 1열에 적힌 글자를 세로로 읽으면 programmers입니다. 따라서 "programmers"를 return 합니다.

## 풀이

```js
function solution(my_string, m, c) {
    var answer = '';
    
    // c-1번째 열의 문자들을 직접 추출
    for (let i = c - 1; i < my_string.length; i += m) {
        answer += my_string[i];
    }
    
    return answer;
}
```
