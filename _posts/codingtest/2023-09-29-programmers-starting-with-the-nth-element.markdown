---
layout: post
title:  "프로그래머스 n 번째 원소부터"
date:   2023-09-29 21:43:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 n 번째 원소부터

### 문제

정수 리스트 `num_list`와 정수 `n`이 주어질 때, `n` 번째 원소부터 마지막 원소까지의 모든 원소를 담은 리스트를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 2 ≤ `num_list`의 길이 ≤ 30
- 1 ≤ `num_list`의 원소 ≤ 9
- 1 ≤ `n` ≤ `num_list`의 길이

### 입출력 예

| num_list | n | result |
| --- | --- |
| `[2, 1, 6]` | `3` | `[6]` |
| `[5, 2, 1, 7, 5]` | `2` | `[2, 1, 7, 5]` |

### 입출력 예 설명

**입출력 예 #1**

- [2, 1, 6]의 세 번째 원소부터 마지막 원소까지의 모든 원소는 [6]입니다.

**입출력 예 #2**

- [5, 2, 1, 7, 5]의 두 번째 원소부터 마지막 원소까지의 모든 원소는 [2, 1, 7, 5]입니다.

### 풀이

```py
def solution(num_list, n):
    return num_list[n-1:]
```