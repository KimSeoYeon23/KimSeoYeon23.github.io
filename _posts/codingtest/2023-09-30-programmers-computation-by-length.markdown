---
layout: post
title:  "프로그래머스 길이에 따른 연산"
date:   2023-09-30 13:32:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 길이에 따른 연산

### 문제

정수가 담긴 리스트 `num_list`가 주어질 때, 리스트의 길이가 11 이상이면 리스트에 있는 모든 원소의 합을 10 이하이면 모든 원소의 곱을 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- 2 <= `num_list`의 길이 <= 20
- 1 <= `num_list`의 원소 <= 9

### 입출력 예

| num_list | result |
| --- | --- |
| `[3, 4, 5, 2, 5, 4, 6, 7, 3, 7, 2, 2, 1]` | `51` |
| `[2, 3, 4, 5]` | `120` |

### 입출력 예 설명

**입출력 예 #1**

- 리스트의 길이가 13이므로 모든 원소의 합인 51을 return합니다.

**입출력 예 #2**

- 리스트의 길이가 4이므로 모든 원소의 곱인 120을 return합니다.

### 풀이

```py
def solution(num_list):
    multiple = 1
    if len(num_list) >= 11:
        return sum(num_list)
    else:
        for i in num_list:
            multiple *= i
        return multiple
```