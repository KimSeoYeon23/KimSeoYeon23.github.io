---
layout: post
title:  "프로그래머스 조건에 맞게 수열 변환하기 3"
date:   2023-09-27 23:09:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 조건에 맞게 수열 변환하기 3

### 문제

정수 배열 `arr`와 자연수 `k`가 주어집니다.

만약 `k`가 홀수라면 `arr`의 모든 원소에 `k`를 곱하고, `k`가 짝수라면 `arr`의 모든 원소에 `k`를 더한다.

이러한 변환을 마친 후의 `arr`을 return 하는 solution 함수를 완해 주세요.

### 제한사항

- 1 <= `arr`의 길이 <= 1,000,000
  - 1 <= `arr`의 원소의 값 <= 100
- 1 <= `k` <= 100

### 입출력 예

| arr | k | result |
| --- | --- | --- |
| `[1, 2, 3, 100, 99, 98]` | `3` | `[3, 6, 8, 300, 297, 294]` |
| `[1, 2, 3, 100, 99, 98]` | `2` | `[3, 4, 5, 102, 101, 100]` |

### 입출력 예 설명

**입출력 예 #1**

- 주어진 `k`인 3은 홀수이므로, 전체 배열에 3을 곱합니다. 따라서 [3, 6, 8, 300, 297, 294]을 return 합니다.

**입출력 예 #2**
  
- 주어진 `k`인 2는 짝수이므로, 전체 배열에 2를 더합니다. 따라서 [3, 4, 5, 102, 101, 100]을 return 합니다.

### 풀이

```py
def solution(arr, k):
    result = []
    
    if k % 2 == 0:
        result = [num + k for num in arr]
    else:
        result = [num * k for num in arr]
    return result
```