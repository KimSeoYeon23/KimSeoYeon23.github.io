---
layout: post
title:  "프로그래머스 배열 자르기"
date:   2023-10-23 22:06:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 배열 자르기

### 문제

정수 배열 `numbers`와 정수 `num1`, `num2`가 매개변수로 주어질 때, `numbers`의 `num`번 째 인덱스부터 `num2`번째 인덱스까지 자른 정수 배열을 return 하도록 solution 함수를 완성해보세요.

### 제한사항

- 2 <= `numbers`의 길이 <= 30
- 0 <= `numbers`의 원소 <= 1,000
- 0 <= `num1` < `num2` < `numbers`의 길이

### 입출력 예

| numbers | num1 | num2 | result |
| --- | --- | --- | --- |
| `[1, 2, 3, 4, 5]` | `1` | `3` | `[2, 3, 4]` |
| `[1, 3, 5]` | `1` | `2` | `[3, 5]` | 

### 입출력 예 설명

**입출력 예 #1**

- [1, 2, 3, 4, 5]의 1번쨰 인덱스 2부터 3번째 인덱스 4까지 자른 [2, 3, 4]를 return 합니다.

**입출력 예 #2**

- [1, 3, 5]의 1번째 인덱스 3부터 2번쨰 인덱스 5까지 자른 [3, 5]를 return 합니다.

### 풀이

```py
def solution(numbers, num1, num2):
    return numbers[num1:num2+1]
```