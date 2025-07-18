---
layout: post
title:  "프로그래머스 짝수 홀수 개수"
date:   2023-10-24 20:37:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 짝수 홀수 개수

### 문제

정수가 담긴 리스트 `num_list`가 주어질 때, `num_list`의 원소 중 짝수와 홀수의 개수를 담은 배열을 return 하도록 solution 함수를 완성해보세요.

### 제한사항

- 1 <= `num_list`의 길이 <= 100
- 0 <= `num_list`의 원소 <= 1,000

### 입출력 예

| num_list | result |
| --- | --- |
| `[1, 2, 3, 4, 5]` | `[2, 3]` |
| `[1, 3, 5, 7]` | `[0, 4]` |

### 입출력 예 설명

**입출력 예 #1**

- [1, 2, 3, 4, 5]에는 짝수가 2, 4로 두 개, 홀수가 1, 3, 5로 세 개 있습니다.

**입출력 예 #2**

- [1, 3, 5, 7]에는 짝수가 없고 홀수가 네 개 있습니다.

### 풀이

```py
def solution(num_list):
    even = 0
    odd = 0
    for i in num_list:
        if i % 2 == 0:
            even += 1
        else:
            odd += 1
    return [even, odd]
```