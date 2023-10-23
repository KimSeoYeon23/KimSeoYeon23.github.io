---
layout: post
title:  "프로그래머스 순서쌍의 개수"
date:   2023-10-23 21:51:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 순서쌍의 개수

### 문제

순서쌍이란 두 개의 숫자를 순서를 정하여 짝지어 나타낸 쌍으로 (a, b)로 표기합니다. 자연수 `n`이 매개변수로 주어질 때 두 숫자의 곱이 `n`인 자연수 순서쌍의 개수를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 1 <= n <= 1,000,000

### 입출력 예

| n | result |
| --- | --- |
| `20` | `6` |
| `100` | `9` |

### 입출력 예 설명

**입출력 예 #1**

- `n`이 20이므로 곱이 20인 순서쌍은 (1, 20), (2, 10), (4, 5), (5, 4), (10, 2), (20, 1) 이므로 6을 return합니다.

**입출력 예 #2**

- `n`이 100 이므로 곱이 100인 순서쌍은 (1, 100), (2, 50), (4, 25), (5, 20), (10, 10), (20, 5), (25, 4), (50, 2), (100, 1) 이므로 9를 return합니다.

### 풀이

```py
def solution(n):
    answer = 0
    for i in range(1, n+1):
        j = n % i
        if j == 0:
            answer += 1
        else:
            continue
    return answer
```