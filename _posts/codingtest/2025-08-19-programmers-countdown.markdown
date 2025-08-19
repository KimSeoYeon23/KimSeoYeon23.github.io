---
layout: post
title:  "카운트다운"
date:   2025-08-19 12:17:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 카운트다운

### 문제

정수 `start_num`와 `end_num`가 주어질 때, `start_num`에서 `end_num`까지 1씩 감소하는 수들을 차례로 담은 리스트를 return하도록 solution 함수를 완성해주세요.

## 제한 사항

- 0 ≤ `end_num` ≤ `start_num` ≤ 50

### 예시

입출력 예 #1

- 10부터 3까지 1씩 감소하는 수를 담은 리스트는 [10, 9, 8, 7, 6, 5, 4, 3]입니다.

## 풀이

- JavaScript

```js
function solution(start_num, end_num) {
    var answer = [];
    for (let i = start_num; i >= end_num; i--)  {
        answer.push(i)
    }
    return answer;
}
```

- python

```python
def solution(start_num, end_num):
    answer = []
    for i in range(start_num, end_num-1, -1):
        answer.append(i)
    return answer
```