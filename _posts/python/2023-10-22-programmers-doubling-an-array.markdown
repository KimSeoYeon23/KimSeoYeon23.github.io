---
layout: post
title:  "프로그래머스 배열 두 배 만들기"
date:   2023-10-22 18:21:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 배열 두 배 만들기

### 문제

정수 배열 `numbers`가 매개변수로 주어집니다. `numbers`의 각 원소에 두 배한 원소를 가진 배열을 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- -10,000 <= `numbers`의 원소 <= 10,000
- 1 <= `numbers`의 길이 <= 1,000

### 입출력 예

| numbers | result |
| --- | --- |
| `[1, 2, 3, 4, 5]` | `[2, 4, 6, 8, 10]` |
| `[1, 2, 100, -99, 1, 2, 3]` | `[2, 4, 200, -198, 2, 4, 6]` |

### 입출력 예 설명

**입출력 예 #1**

- [1, 2, 3, 4, 5]의 각 원소에 두 배를 한 배열 [2, 4, 6, 8, 10]을 return합니다.

**입출력 예 #2**

- [1, 2, 100, -99, 1, 2, 3]의 각 원소에 두 배를 한 배열 [2, 4, 200, -198, 2, 4, 6]을 return합니다.

### 풀이

```py
def solution(numbers):
    answer = []
    for i in numbers:
        answer.append(i * 2)
    return answer
```