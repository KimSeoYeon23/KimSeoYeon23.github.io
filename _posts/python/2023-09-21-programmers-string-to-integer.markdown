---
layout: post
title:  "프로그래머스 문자열을 정수로 변환하기"
date:   2023-09-21 19:11:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 문자열을 정수로 변환하기

### 문제

숫자로만 이루어진 문자열 `n_str`이 주어질 때, `n_str`을 정수로 변환하여 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 1 ≤ `n_str` ≤ 5
- `n_str`은 0부터 9까지의 정수 문자로만 이루어져 있습니다.

### 입출력 예

| n_str | result |
| --- | --- |
| `"10"` | `10` |
| `"8542"` | `8542` |

### 입출력 예 설명

**입출력 예 #1**

- "10"을 정수로 바꾸면 10입니다.

**입출력 예 #2**
  
- "8542"를 정수로 바꾸면 8542입니다.

### 풀이

```py
def solution(n_str):
    return int(n_str)
```