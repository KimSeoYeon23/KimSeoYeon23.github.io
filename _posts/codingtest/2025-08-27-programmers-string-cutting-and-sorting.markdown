---
layout: post
title:  "문자열 잘라서 정렬하기"
date:   2025-08-27 11:55:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 문자열 잘라서 정렬하기

### 문제

문자열 `myString`이 주어집니다. "x"를 기준으로 해당 문자열을 잘라내 배열을 만든 후 사전순으로 정렬한 배열을 return 하는 solution 함수를 완성해 주세요.

단, 빈 문자열은 반환할 배열에 넣지 않습니다.

## 제한 사항

- 1 ≤ `myString` ≤ 100,000
  - `myString`은 알파벳 소문자로 이루어진 문자열입니다.

### 예시

입출력 예 #1

- `myString`을 "x"를 기준으로 자른 배열은 ["a","b","c","d"]이며, 이 배열은 이미 사전순으로 정렬된 상태입니다. 따라서 해당 배열을 return 합니다.

입출력 예 #2

- `myString`을 "x"를 기준으로 자른 배열은 ["d","cc","bbb","aaaa"]이며, 이 배열을 사전순으로 정렬하면 ["aaaa","bbb","cc","d"]입니다. 따라서 해당 배열을 return 합니다.

## 풀이

- JavaScript

```js
function solution(myString) {
    return myString.split("x").filter(s => s !== '').sort();
}
```


- python

```python
def solution(myString):    
    return sorted([v for v in myString.split("x") if v])
```