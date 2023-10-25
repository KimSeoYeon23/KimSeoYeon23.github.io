---
layout: post
title:  "프로그래머스 x만큼 간격이 있는 n개의 숫자"
date:   2023-10-26 00:15:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 x만큼 간격이 있는 n개의 숫자

### 문제

함수 solution은 정수 `x`와 자연수 `n`을 입력 받아, `x`부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

### 제한사항

- `x`는 -10000000 이상, 10000000 이하인 정수입니다.
- `n`은 1000 이하인 자연수입니다.

### 입출력 예

| x | n | answer |
| --- | --- | --- |
| `2` | `5` | `[2, 4, 6, 8, 10]` |
| `4` | `3` | `[4, 8, 12]` |
| `-4` | `2` | `[-4, -8]` |

### 풀이

```py
def solution(x, n):
    answer = []
    for i in range(n):
        answer.append((i+1) * x)
    return answer
```