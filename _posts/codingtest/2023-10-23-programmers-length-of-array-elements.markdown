---
layout: post
title:  "프로그래머스 배열 원소의 길이"
date:   2023-10-23 21:46:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 배열 원소의 길이

### 문제

문자열 배열 `strlist`가 매개변수로 주어집니다. `strlist` 각 원소의 길이를 담은 배열을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 1 <= `strlist` 원소의 길이 <= 100
- `strlist`는 알파벳 소문자, 대문자, 특수문자로 구성되어 있습니다.

### 입출력 예

| array | result |
| --- | --- |
| `["We", "are", "the", "world!"]` | `[2, 3, 3, 6]` |
| `["I", "Love", "Programmers."]` | `[1, 4, 12]` |

### 입출력 예 설명

**입출력 예 #1**

- ["We", "are", "the", "world!"]의 각 원소의 길이인 [2, 3, 3, 6]을 return합니다.

**입출력 예 #2**

- ["I", "Love", "Programmers."]의 각 원소의 길이인 [1, 4, 12]를 return합니다.

### 풀이

```py
def solution(strlist):
    answer = []
    for i in strlist:
        answer.append(len(i))
    return answer
```