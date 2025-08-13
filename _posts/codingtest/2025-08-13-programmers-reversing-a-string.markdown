---
layout: post
title:  "문자열 뒤집기"
date:   2025-08-13 18:32:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}


## 프로그래머스 문자열 뒤집기

### 문제

문자열 `my_string`과 정수 `s`, `e`가 매개변수로 주어질 때, `my_string`에서 인덱스 `s`부터 인덱스 `e`까지를 뒤집은 문자열을 `return` 하는 `solution` 함수를 작성해 주세요.

## 제한 사항

- `my_string`은 숫자와 알파벳으로만 이루어져 있습니다.
- 1 ≤ `my_string`의 길이 ≤ 1,000
- 0 ≤ `s` ≤ `e` < `my_string`의 길이


### 예시

입출력 예 #1

예제 1번의 `my_string`에서 인덱스 6부터 인덱스 12까지를 뒤집은 문자열은 "ProgrammerS123"이므로 "ProgrammerS123"를 return 합니다.

입출력 예 #2

예제 2번의 `my_string`에서 인덱스 4부터 인덱스 10까지를 뒤집으면 원래 문자열과 같은 "Stanley1yelnatS"이므로 "Stanley1yelnatS"를 return 합니다.

## 풀이

```js
function solution(my_string, s, e) {
    var answer = '';
    const sliceString = my_string.slice(s, e+1).split('').reverse().join('')
    answer = my_string.slice(0, s) + sliceString + my_string.slice(e+1)
    
    return answer;
}
```
