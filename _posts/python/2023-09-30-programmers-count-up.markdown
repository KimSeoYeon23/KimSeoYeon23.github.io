---
layout: post
title:  "프로그래머스 카운트 업"
date:   2023-09-30 13:46:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 카운트 업

### 문제

정수 `start_num`와 `end_num`이 주어질 때, `start_num`부터 `end_num`까지의 숫자를 차례로 담은 리스트를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `start_num` <= `end_num` <= 50

### 입출력 예

| start_num | end_num | result |
| --- | --- | --- |
| `3` | `10` | `[3, 4, 5, 6, 7, 8, 9, 10]` |

### 입출력 예 설명

**입출력 예 #1**

- 3부터 10까지의 숫자들을 담은 리스트 [3, 4, 5, 6, 7, 8, 9, 10]를 return합니다.

### 풀이

```py
def solution(start_num, end_num):
    result = []
    for i in range(start_num, end_num+1):
        result.append(i)
    return result

# or

def solution(start_num, end_num):
    return list(range(start_num, end_num + 1))
```