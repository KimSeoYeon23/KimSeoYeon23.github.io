---
layout: post
title:  "프로그래머스 정수 부분"
date:   2023-09-29 21:40:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 정수 부분

### 문제

실수 `flo`가 매개 변수로 주어질 때, `flo`의 정수 부분을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `flo` <= 100

### 입출력 예

| flo | result |
| --- | --- |
| `1.42` | `1` |
| `69.32` | `69` |

### 입출력 예 설명

**입출력 예 #1**

- 1.42의 정수 부분은 1입니다.

**입출력 예 #2**

- 69.32의 정수 부분은 69입니다.

### 풀이

```py
import math

def solution(flo):
    return math.floor(flo)
```