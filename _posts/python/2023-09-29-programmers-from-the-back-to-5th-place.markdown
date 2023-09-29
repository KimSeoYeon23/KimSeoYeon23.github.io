---
layout: post
title:  "프로그래머스 뒤에서 5등 위로"
date:   2023-09-29 21:25:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 뒤에서 5등 위로

### 문제

정수로 이루어진 리스트 `num_list`가 주어집니다. `num_list`에서 가장 작은 5개의 수를 제외한 수들을 오름차순으로 담은 리스트를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 6 <= `num_list`의 길이 <= 30
- 1 <= `num_list`의 원소 <= 100

### 입출력 예

| num_list | result |
| --- | --- |
| `[12, 4, 15, 46, 38, 1, 14, 56, 32, 10]` | `[15, 32, 38, 46, 56]` |

### 입출력 예 설명

**입출력 예 #1**

- [12, 4, 15, 46, 38, 1, 14, 56, 32, 10]를 정렬하면 [1, 4, 10, 12, 14, 15, 32, 38, 46, 56]이 되고, 앞에서부터 6번째 이후의 수들을 고르면 [15, 32, 38, 46, 56]가 됩니다.

### 풀이

```py
def solution(num_list):
    num_list.sort()
    return num_list[5:]

```