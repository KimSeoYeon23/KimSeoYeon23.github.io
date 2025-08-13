---
layout: post
title:  "접미사인지 확인하기"
date:   2025-08-13 18:46:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 접미사인지 확인하기

### 문제

어떤 문자열에 대해서 접미사는 특정 인덱스부터 시작하는 문자열을 의미합니다. 예를 들어, "banana"의 모든 접미사는 "banana", "anana", "nana", "ana", "na", "a"입니다.
문자열 `my_string`과 `is_suffix`가 주어질 때, `is_suffix`가 `my_string`의 접미사라면 1을, 아니면 0을 return 하는 solution 함수를 작성해 주세요.

## 제한 사항

- 1 ≤ `my_string`의 길이 ≤ 100
- 1 ≤ `is_suffix`의 길이 ≤ 100
- `my_string`과 `is_suffix`는 영소문자로만 이루어져 있습니다.


### 예시

입출력 예 #1

예제 1번에서 `is_suffix`가 `my_string`의 접미사이기 때문에 1을 return 합니다.

입출력 예 #2

예제 2번에서 `is_suffix`가 `my_string`의 접미사가 아니기 때문에 0을 return 합니다.

입출력 예 #3

예제 3번에서 `is_suffix`가 `my_string`의 접미사가 아니기 때문에 0을 return 합니다.

입출력 예 #4

예제 4번에서 `is_suffix`가 `my_string`의 접미사가 아니기 때문에 0을 return 합니다.

## 풀이

```js
function solution(my_string, is_suffix) {
    const suffix = []
    for (let i = 0; i < my_string.length; i++) {
        suffix.push(my_string.substr(i, my_string.length))
    }
    
    return suffix.includes(is_suffix) ? 1 : 0
}
```
