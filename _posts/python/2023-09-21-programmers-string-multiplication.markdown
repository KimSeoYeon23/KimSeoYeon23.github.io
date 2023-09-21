---
layout: post
title:  "프로그래머스 문자열 곱하기"
date:   2023-09-21 19:05:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 문자열 곱하기

### 문제

문자열 `my_string`과 정수 `k`가 주어질 때, `my_string`을 `k`번 반복한 문자열을 return 하는 solution 함수를 작성해 주세요.

### 제한사항

- 1 <= `my_string`의 길이 <= 100
- `my_string`의 영소문자로만 이루어져 있습니다.
- 1 <= `k` <= 100

### 입출력 예

| my_string | k | result |
| --- | --- | --- |
| `"string"` | 3 | `"stringstringstring"` |
| `"lov"` | 10 |`"lovelovelovelovelovelovelovelovelovelove"` |

### 입출력 예 설명

**입출력 예 #1**

- 예제 1번의 `my_string`은 "string"이고 이를 3번 반복한 문자열은 "stringstringstring"이므로 이를 return 합니다.

**입출력 예 #2**
  
- 예제 2번의 `my_string`은 "love"이고 이를 10번 반복한 문자열은 "lovelovelovelovelovelovelovelovelovelove"이므로 이를 return 합니다.

### 풀이

```py
def solution(my_string, k):
    result = ""
    for _ in range(k):
        result += my_string
    return result

# or

def solution(my_string, k):
    return my_string * k
```