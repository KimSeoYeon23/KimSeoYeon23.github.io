---
layout: post
title:  "프로그래머스 문자열의 앞의 n글자"
date:   2023-09-27 22:22:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 문자열의 앞의 n글자

### 문제

문자열 `my_string`과 정수 `n`이 매개변수로 주어질 때, `my_string`의 앞의 `n`글자로 이루어진 문자열을 return 하는 solution 함수를 작성해 주세요.

### 제한사항

- `my_string`은 수자와 알파벳으로 이루어져 있습니다.
- 1 <= `my_string`의 길이 <= 1,000
- 1 <= `n` <= `my_string`의 길이

### 입출력 예

| my_string | n | result |
| --- | --- | --- |
| `"ProgrammerS123"` | `11` | `"ProgrammerS"` |
| `"He110W0r1d"` | `5` | `He110` |

### 입출력 예 설명

**입출력 예 #1**

- 예제 1번의 `my_string`에서 앞의 11글자는 "ProgrammerS"이므로 이 문자열을 return 합니다.

**입출력 예 #2**
  
- 예제 2번의 `my_string`에서 앞의 5글자는 "He110"이므로 이 문자열을 return 합니다.

### 풀이

```py
def solution(my_string, n):
    return my_string[0:n]
```