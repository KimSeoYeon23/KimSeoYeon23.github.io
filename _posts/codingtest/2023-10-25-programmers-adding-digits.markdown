---
layout: post
title:  "프로그래머스 자릿수 더하기"
date:   2023-10-25 23:11:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 자릿수 더하기

### 문제

정수 `n`이 매개변수로 주어질 때 `n`의 각 자리 숫자의 합을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `n` <= 1,000,000

### 입출력 예

| n | result |
| --- | --- |
| `1234` | `10` |
| `930211` | `16` |

### 입출력 예 설명

**입출력 예 #1**

- 1 + 2 + 3 + 4 = 10을 return합니다.

**입출력 예 #2**

- 9 + 3 + 0 + 2 + 1 + 1 = 16을 return합니다.

### 풀이

```py
def solution(n):
    answer = 0
    str_num = str(n)
    for i in str_num:
        answer += int(i)
    return answer
```