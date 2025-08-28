---
layout: post
title:  "2의 영역"
date:   2025-08-19 17:00:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 2의 영역

### 문제

정수 배열 `arr`가 주어집니다. 배열 안의 2가 모두 포함된 가장 작은 연속된 부분 배열을 return 하는 solution 함수를 완성해 주세요.

단, `arr`에 2가 없는 경우 [-1]을 return 합니다.

## 제한 사항

- 1 ≤ `arr`의 길이 ≤ 100,000
    - 1 ≤ `arr`의 원소 ≤ 10

### 예시

입출력 예 #1

- 2가 있는 인덱스는 1번, 5번 인덱스뿐이므로 1번부터 5번 인덱스까지의 부분 배열인 [2, 1, 4, 5, 2]를 return 합니다.

입출력 예 #2

- 2가 한 개뿐이므로 [2]를 return 합니다.

입출력 예 #3

- 2가 배열에 없으므로 [-1]을 return 합니다.

입출력 예 #4

- 2가 있는 인덱스는 1번, 3번, 6번 인덱스이므로 1번부터 6번 인덱스까지의 부분 배열인 [2, 1, 2, 1, 10, 2]를 return 합니다.

## 풀이

- JavaScript

```js
function solution(arr) {
    var answer = [];
    const first = arr.indexOf(2)
    const last = arr.lastIndexOf(2)
    answer = arr.slice(first, last+1).length ? arr.slice(first, last+1) : [-1]
    return answer;
}
```

- python

```python
def solution(arr):
    answer = []
    reverse_arr = arr[::-1]
    
    if 2 not in arr:
        return [-1]
    
    first = arr.index(2)
    last = len(arr) - 1 - reverse_arr.index(2)
    
    return arr[first:last+1]
```