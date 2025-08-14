---
layout: post
title:  "접미사 배열"
date:   2025-08-13 18:39:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 접미사 배열

### 문제

어떤 문자열에 대해서 접미사는 특정 인덱스부터 시작하는 문자열을 의미합니다. 예를 들어, "banana"의 모든 접미사는 "banana", "anana", "nana", "ana", "na", "a"입니다.
문자열 `my_string`이 매개변수로 주어질 때, `my_string`의 모든 접미사를 사전순으로 정렬한 문자열 배열을 return 하는 solution 함수를 작성해 주세요.

## 제한 사항

- `my_string`은 알파벳 소문자로만 이루어져 있습니다.
- 1 ≤ `my_string`의 길이 ≤ 100


### 예시

입출력 예 #1

예제 1번의 `my_string`는 "banana"로 모든 접미사는 문제의 설명과 같습니다. 이를 사전순으로 정렬하면 "a", "ana", "anana", "banana", "na", "nana"이므로 ["a", "ana", "anana", "banana", "na", "nana"]를 return 합니다.

입출력 예 #2

예제 2번의 `my_string`는 "programmers"이고 모든 접미사는 "programmers", "rogrammers", "ogrammers", "grammers", "rammers", "ammers", "mmers", "mers", "ers", "rs", "s"입니다. 이를 사전순으로 정렬한 문자열 배열 ["ammers", "ers", "grammers", "mers", "mmers", "ogrammers", "programmers", "rammers", "rogrammers", "rs", "s"]를 return 합니다.

## 풀이

```js
function solution(my_string) {
    var answer = [];
        
    for (let i = 0; i < my_string.length; i++) {
        answer.push(my_string.substr(i, my_string.length))
    }
    return answer.sort();
}
```
