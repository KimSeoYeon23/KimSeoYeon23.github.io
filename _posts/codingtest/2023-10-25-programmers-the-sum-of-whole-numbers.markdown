---
layout: post
title:  "프로그래머스 약수의 합"
date:   2023-10-25 23:18:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 약수의 합

### 문제

정수 `n`을 입력받아 `n`의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

### 제한사항

- `n`은 0 이상 3000이하인 정수입니다.

### 입출력 예

| n | result |
| --- | --- |
| `12` | `28` |
| `5` | `6` |

## 입출력 예 설명

**입출력 예 #1**

- 12의 약수는 1, 2, 3, 4, 6, 12입니다. 이를 모두 더하면 28입니다.

**입출력 예 #2**

- 5의 약수는 1, 5입니다. 이를 모두 더하면 6입니다.

### 풀이

```py
def solution(n):
    answer = 0
    for i in range(1, n+1):
        if n % i == 0:
            answer += i
    return answer
```