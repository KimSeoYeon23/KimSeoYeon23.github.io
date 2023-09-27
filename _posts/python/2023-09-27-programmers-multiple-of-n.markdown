---
layout: post
title:  "프로그래머스 n의 배수"
date:   2023-09-27 22:27:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 n의 배수

### 문제

정수 `num`과 `n`이 매개 변수로 주어질 때, `num`이 `n`의 배수이면 1을 return, `n`의 배수가 아니라면 0을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 2 <= `num` <= 100
- 2 <= `n` <= 9

### 입출력 예

| num | n | result |
| --- | --- | --- |
| `98` | `2` | `1` |
| `34` | `3` | `0` |

### 입출력 예 설명

**입출력 예 #1**

- 98은 2의 배수이므로 1을 return합니다.

**입출력 예 #2**
  
- 32는 3의 배수가 아니므로 0을 return합니다.

### 풀이

```py
def solution(num, n):
    if num % n == 0:
        return 1
    else:
        return 0
```