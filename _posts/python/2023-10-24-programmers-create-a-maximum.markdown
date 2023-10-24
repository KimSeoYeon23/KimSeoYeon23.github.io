---
layout: post
title:  "프로그래머스 최댓값 만들기 (1)"
date:   2023-10-24 20:27:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 최댓값 만들기 (1)

### 문제

정수 배열 `numbers`가 매개변수로 주어집니다. `numbers`의 원소 중 두 개를 곱해 만들 수 있는 최댓값을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `numbers`의 원소 <= 10,000
- 2 <= `numbers`의 길이 <= 100

### 입출력 예

| numbers | result |
| --- | --- |
| `[1, 2, 3, 4, 5]` | `20` |
| `[0, 31, 24, 10, 1, 9]` | `744` |

### 입출력 예 설명

**입출력 예 #1**

- 두 수의 곱중 최댓값은 4 * 5 = 20 입니다.

**입출력 예 #2**

- 두 수의 곱중 최댓값은 31 * 24 = 744 입니다.

### 풀이

```py
def solution(numbers):
    numbers.sort(reverse=True)
    return numbers[0] * numbers[1]
```