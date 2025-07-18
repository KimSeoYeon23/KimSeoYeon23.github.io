---
layout: post
title:  "프로그래머스 이어 붙인 수"
date:   2023-09-30 13:40:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 이어 붙인 수

### 문제

정수가 담긴 리스트 `num_list`가 주어집니다. `num_list`의 홀수만 순서대로 이어 붙인 수와 짝수만 순서대로 이어 붙인 수의 합을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 2 <= `num_list`의 길이 <= 10
- 1 <= `num_list`의 원소 <= 9
- `num_list`에는 적어도 한 개씩의 짝수와 홀수가 있습니다.

### 입출력 예

| num_list | result |
| --- | --- |
| `[3, 4, 5, 2, 1]	` | `393` |
| `[5, 7, 8, 3]` | `581` |

### 입출력 예 설명

**입출력 예 #1**

- 홀수만 이어 붙인 수는 351이고 짝수만 이어 붙인 수는 42입니다. 두 수의 합은 393입니다.

**입출력 예 #2**

- 홀수만 이어 붙인 수는 573이고 짝수만 이어 붙인 수는 8입니다. 두 수의 합은 581입니다.

### 풀이

```py
def solution(num_list):
    a = ''
    b = ''
    for i in num_list:
        if i % 2 == 0:
            a += str(i)
        else:
            b += str(i)
    return int(a) + int(b)
```