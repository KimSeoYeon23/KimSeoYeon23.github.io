---
layout: post
title:  "문자열 바꿔서 찾기"
date:   2025-08-29 13:59:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 문자열 바꿔서 찾기

### 문제

문자 "A"와 "B"로 이루어진 문자열 `myString`과 `pat`가 주어집니다. `myString`의 "A"를 "B"로, "B"를 "A"로 바꾼 문자열의 연속하는 부분 문자열 중 `pat`이 있으면 1을 아니면 0을 return 하는 solution 함수를 완성하세요.

## 제한 사항

- 1 ≤ `myString`의 길이 ≤ 100
- 1 ≤ `pat`의 길이 ≤ 10
- `myString`과 `pat`는 문자 "A"와 "B"로만 이루어진 문자열입니다.

### 예시

입출력 예 #1

- "ABBAA"에서 "A"와 "B"를 서로 바꾸면 "BAABB"입니다. 여기에는 부분문자열 "AABB"가 있기 때문에 1을 return 합니다.

입출력 예 #2

- "ABAB"에서 "A"와 "B"를 서로 바꾸면 "BABA"입니다. 여기에는 부분문자열 "BABA"가 없기 때문에 0을 return 합니다.

## 풀이

- JavaScript

```js
function solution(myString, pat) {
    let text = ''
    for (let i = 0; i < myString.length; i++) {
        if (myString[i] === 'A') {
            text += 'B'
        } else {
            text += 'A'
        }
    }
    return Number(text.includes(pat))
}
```


- python

```python
def solution(myString, pat):
    text = ''
    for str in myString:
        if str == "A":
            text += "B"
        else:
            text += "A"
    return int(pat in text)
```