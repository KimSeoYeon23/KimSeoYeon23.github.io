---
layout: post
title:  "배열 만들기3"
date:   2025-08-19 12:17:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 배열 만들기3

### 문제

정수 배열 `arr`와 2개의 구간이 담긴 배열 `intervals`가 주어집니다.

`intervals`는 항상 `[[a1, b1], [a2, b2]]`의 꼴로 주어지며 각 구간은 닫힌 구간입니다. 닫힌 구간은 양 끝값과 그 사이의 값을 모두 포함하는 구간을 의미합니다.

이때 배열 `arr`의 첫 번째 구간에 해당하는 배열과 두 번째 구간에 해당하는 배열을 앞뒤로 붙여 새로운 배열을 만들어 return 하는 solution 함수를 완성해 주세요.

## 제한 사항

- 1 ≤ `arr`의 길이 ≤ 100,000
- 1 ≤ `arr`의 원소 < 100
- 1 ≤ `a1` ≤ `b1` < `arr`의 길이
- 1 ≤ `a2` ≤ `b2` < `arr`의 길이

### 예시

입출력 예 #1

첫 번째 구간에 해당하는 배열은 [2, 3, 4] 입니다.
두 번째 구간에 해당하는 배열은 [1, 2, 3, 4, 5] 입니다.
따라서 이 두 배열을 앞뒤로 붙인 배열인 [2, 3, 4, 1, 2, 3, 4, 5]를 return 합니다.

## 풀이

- JavaScript

```js
function solution(arr, intervals) {
    var answer = [];
    const [[a,b],[c,d]] = intervals;    
    
    return [...arr.slice(a, b+1), ...arr.slice(c, d+1)];
}
```

- python

```python
def solution(arr, intervals):
    answer = []
    answer.append(arr[intervals[0][0]:intervals[0][1]+1])
    answer.append(arr[intervals[1][0]:intervals[1][1]+1])
    return sum(answer, [])
```