---
layout: post
title:  "리스트 자르기"
date:   2025-08-19 12:17:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 리스트 자르기

### 문제

정수 `n`과 정수 3개가 담긴 리스트 `slicer` 그리고 정수 여러 개가 담긴 리스트 `num_list`가 주어집니다. `slicer`에 담긴 정수를 차례대로 a, b, c라고 할 때, `n`에 따라 다음과 같이 `num_list`를 슬라이싱 하려고 합니다.

- `n` = 1 : `num_list`의 0번 인덱스부터 `b`번 인덱스까지
- `n` = 2 : `num_list`의 `a`번 인덱스부터 마지막 인덱스까지
- `n` = 3 : `num_list`의 `a`번 인덱스부터 `b`번 인덱스까지
- `n` = 4 : `num_list`의 `a`번 인덱스부터 `b`번 인덱스까지 c 간격으로

올바르게 슬라이싱한 리스트를 return하도록 solution 함수를 완성해주세요.

## 제한 사항

- `n` 은 1, 2, 3, 4 중 하나입니다.
- `slicer`의 길이 = 3
- `slicer`에 담긴 정수를 차례대로 a, b, c라고 할 때
    - 0 ≤ a ≤ b ≤ `num_list`의 길이 - 1
    - 1 ≤ c ≤ 3
- 5 ≤ `num_list`의 길이 ≤ 30
- 0 ≤ `num_list`의 원소 ≤ 100

### 예시

입출력 예 #1

- [1, 2, 3, 4, 5, 6, 7, 8, 9]에서 1번 인덱스부터 5번 인덱스까지 자른 리스트는 [2, 3, 4, 5, 6]입니다.

입출력 예 #2

- [1, 2, 3, 4, 5, 6, 7, 8, 9]에서 1번 인덱스부터 5번 인덱스까지 2개 간격으로 자른 리스트는 [2, 4, 6]입니다.

## 풀이

- JavaScript

```js
function solution(n, slicer, num_list) {
    var answer = [];
    switch (n) {
        case 1:
            answer = num_list.slice(0, slicer[1]+1)
            break
        case 2:
            answer = num_list.slice(slicer[0])
            break
        case 3:
            answer = num_list.slice(slicer[0], slicer[1]+1)
            break
        default:
            for (let i=slicer[0]; i <= slicer[1]; i += slicer[2]) {
                answer.push(num_list[i])
            }
            break
    }
    return answer;
}
```

- python

```python
def solution(n, slicer, num_list):
    answer = []
    if n == 1:
        answer = num_list[0:slicer[1]+1]
    elif n == 2:
        answer = num_list[slicer[0]:]
    elif n == 3:
        answer = num_list[slicer[0]:slicer[1]+1]
    else:
        answer = num_list[slicer[0]:slicer[1]+1:slicer[2]]
    return answer
```