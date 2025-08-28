---
layout: post
title:  "순서 바꾸기"
date:   2025-08-27 11:41:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 순서 바꾸기

### 문제

정수 리스트 `num_list`와 정수 n이 주어질 때, `num_list`를 `n` 번째 원소 이후의 원소들과 `n` 번째까지의 원소들로 나눠 `n` 번째 원소 이후의 원소들을 `n` 번째까지의 원소들 앞에 붙인 리스트를 return하도록 solution 함수를 완성해주세요.

## 제한 사항

- 2 ≤ `num_list`의 길이 ≤ 30
- 1 ≤ `num_list`의 원소 ≤ 9
- 1 ≤ `n` ≤ `num_list`의 길이

### 예시

입출력 예 #1

- [2, 1, 6]에서 첫 번째 이후의 원소는 [1, 6]이고 첫 번째까지의 원소는 [2]입니다. 두 리스트를 이어 붙이면 [1, 6, 2]가 됩니다.

입출력 예 #2

- [5, 2, 1, 7, 5]에서 세 번째 이후의 원소는 [7, 5]이고 세 번째까지의 원소는 [5, 2, 1]입니다. 두 리스트를 이어 붙이면 [7, 5, 5, 2, 1]가 됩니다.

## 풀이

- JavaScript

```js
function solution(num_list, n) {
    var answer = [];
    answer.push(num_list.slice(n))
    answer.push(num_list.slice(0, n))
    return answer.flat();
}
```


- python

```python
def solution(num_list, n):
    answer = []
    answer.append(num_list[n:])
    answer.append(num_list[:n])
    return sum(answer, [])
```