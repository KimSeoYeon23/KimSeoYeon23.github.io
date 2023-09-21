---
layout: post
title:  "프로그래머스 공배수"
date:   2023-09-21 19:16:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 공배수

### 문제

정수 `number`와 `n`, `m`이 주어집니다. `number`가 `n`의 배수이면서 `m`의 배수이면 1을 아니라면 0을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 10 <= `number` <= 100
- 2 <= `n`, `m` < 10

### 입출력 예

| number | n | m | result |
| --- | --- | --- | --- |
| `60` | `2` | `3` | `1` |
| `55` | `10` | `5` | `0` |

### 입출력 예 설명

**입출력 예 #1**

- 60은 2의 배수이면서 3의 배수이기 때문에 1을 return합니다.

**입출력 예 #2**
  
- 55는 5의 배수이지만 10의 배수가 아니기 때문에 0을 return합니다.

### 풀이

```py
def solution(number, n, m):
    if number % n == 0 and number % m == 0:
        return 1
    else:
        return 0
```