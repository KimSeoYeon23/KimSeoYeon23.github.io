---
layout: post
title:  "프로그래머스 짝수와 홀수"
date:   2023-10-25 23:16:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 짝수와 홀수

### 문제

정수 `num`이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.

### 제한사항

- `num`은 int 범위의 정수입니다.
- 0은 짝수입니다.

### 입출력 예

| num | result |
| --- | --- |
| `3` | `Odd` |
| `4` | `Even` |

### 풀이

```py
def solution(num):
    if num % 2 == 0:
        return "Even"
    else:
        return "Odd"
```