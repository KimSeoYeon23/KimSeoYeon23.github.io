---
layout: post
title:  "프로그래머스 몫 구하기"
date:   2023-09-19 21:10:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 몫 구하기

### 문제

정수 `num1`, `num2`가 매개변수로 주어질 때, `num1`를 `num2`로 나눈 몫을 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `num1` <= 100
- 0 <= `num2` <= 100

### 입출력 예

| num1 | num2 |	result |
| --- | --- | --- |
| `10` | `5` |	`2` |
| `7` | `2` |	`3` |

### 입출력 예 설명

**입출력 예 #1**
- `num1`이 10, `num2`가 5이므로 10을 5로 나눈 몫 2를 return합니다.

**입출력 예 #2**
- `num1`이 7, `num2`가 2이므로 7을 2로 나눈 몫 3을 return합니다.

### 풀이

```py
def solution(num1, num2):
    return num1 // num2
```