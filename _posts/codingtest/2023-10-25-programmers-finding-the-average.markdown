---
layout: post
title:  "프로그래머스 평균 구하기"
date:   2023-10-25 23:28:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 평균 구하기

### 문제

정수를 담고 있는 배열 `arr`의 평균값을 return하는 함수, solution을 완성해보세요.

### 제한사항

- `arr`은 길이 1 이상, 100 이하인 배열입니다.
- `arr`의 원소는 -10,000 이상 10,000 이하인 정수입니다.

### 입출력 예

| arr | result |
| --- | --- |
| `[1, 2, 3, 4]` | `2.5` |
| `[5, 5]` | `5` |

### 풀이

```py
def solution(arr):
    answer = 0
    for i in arr:
        answer += i
    return answer / len(arr)

# or

def solution(arr):
    return sum(arr) / len(arr)
```