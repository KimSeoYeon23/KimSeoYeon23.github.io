---
layout: post
title:  "프로그래머스 flag에 따라 다른 값 반환하기"
date:   2023-09-21 18:55:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 flag에 따라 다른 값 반환하기

### 문제

두 정수 `a`, `b`와 boolean 변수 `flag`가 매개변수로 주어질 때, `flag`가 true면 `a` + `b`를 false면 `a` - `b`를 return 하는 solution 함수를 작성해 주세요.

### 제한사항

- -1,000 <= `a`, `b` <= 1,000

### 입출력 예

| a | b |	flag | result |
| --- | --- | --- | --- |
| `-4` | `7` | `true` | `3` |
| `-4` | `7` | `false` | `-11` |

### 입출력 예 설명

**입출력 예 #1**

- 예제 1번에서 `flag`가 true이므로 `a` + `b` = (-4) + 7 = 3을 return 한다.

**입출력 예 #2**
  
- 예제 2번에서 `flag`가 false이므로 `a` - `b` = (-4) - (7) = -11을 return 한다.

### 풀이

```py
def solution(a, b, flag):
    if flag:
        return a+b
    else:
        return a-b
```