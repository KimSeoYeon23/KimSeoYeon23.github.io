---
layout: post
title:  "프로그래머스 원소들의 곱과 합"
date:   2023-09-27 23:21:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 원소들의 곱과 합

### 문제

정수가 담긴 리스트 `num_list`가 주어질 때, 모든 원소들의 곱이 모든 원소들의 합의 제곱보다 작으면 1을 크면 0을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 2 <= `num_list`의 길이 <= 10
- 1 <= `num_list`의 원소 <= 9

### 입출력 예

| num_list | result |
| --- | --- |
| `[3, 4, 5, 2, 1]` | `1` |
| `[5, 7, 8, 3]` | `0` |

### 입출력 예 설명

**입출력 예 #1**

- 모든 원소의 곱은 120, 합의 제곱은 225이므로 1을 return합니다.

**입출력 예 #2**
  
- 모든 원소의 곱은 840, 합의 제곱은 529이므로 0을 return합니다.

### 풀이

```py
def solution(num_list):
    multiple = 1
    
    for i in num_list:
        multiple *= i
    
    if multiple < sum(num_list) ** 2:
        return 1
    else:
        return 0
    
```