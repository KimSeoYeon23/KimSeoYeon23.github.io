---
layout: post
title:  "프로그래머스 중복된 숫자 개수"
date:   2023-10-22 18:16:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 중복된 숫자 개수

### 문제

정수가 담긴 배열 `array`와 정수 `n`이 매개변수로 주어질 때, `array`에 `n`이 몇 개 있는지를 return 하도록 solution 함수를 완성해보세요.

### 제한사항

- 1 <= `array`의 길이 <= 100
- 0 <= `array`의 원소 <= 1,000
- 0 <= `n` <= 1,000

### 입출력 예

| array | n | result |
| --- | --- | --- |
| `[1, 1, 2, 3, 4, 5]` | `1` | `2` |
| `[0, 2, 3, 4]` | `1` | `0` |

### 입출력 예 설명

**입출력 예 #1**

- [1, 1, 2, 3, 4, 5] 에는 1이 2개 있습니다.

**입출력 예 #2**

- [0, 2, 3, 4]에는 1이 0개 있습니다.

### 풀이

```py
def solution(array, n):
    return array.count(n)
```