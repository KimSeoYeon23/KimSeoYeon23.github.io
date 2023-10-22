---
layout: post
title:  "프로그래머스 짝수의 합"
date:   2023-10-22 17:54:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 짝수의 합

### 문제

정수 `n`이 주어질 때, `n`이하의 짝수를 모두 더한 값을 return 하도록 solution 함수를 작성해주세요.

### 제한사항

0 < `n` <= 1000

### 입출력 예

| n | result |
| --- | --- |
| `10` | `30` |
| `4` | `6` |

### 입출력 예 설명

**입출력 예 #1**

- `n`이 10이므로 2 + 4 + 6 + 8 + 10 = 30을 return 합니다.

**입출력 예 #2**

- `n`이 4이므로 2 + 4 = 6을 return합니다.

### 풀이

```py
def solution(n):
    result = 0
    for i in range(1, n+1):
        if i % 2 == 0:
            result += i
    return result
```