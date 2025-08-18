---
layout: post
title:  "가까운 1 찾기"
date:   2025-08-18 18:48:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 가까운 1 찾기

### 문제

정수 배열 `arr`가 주어집니다. 이때 `arr`의 원소는 1 또는 0입니다. 정수 `idx`가 주어졌을 때, `idx`보다 크면서 배열의 값이 1인 가장 작은 인덱스를 찾아서 반환하는 solution 함수를 완성해 주세요.

단, 만약 그러한 인덱스가 없다면 -1을 반환합니다.

## 제한 사항

- 3 ≤ `arr`의 길이 ≤ 100'000
    - `arr`의 원소는 전부 1 또는 0입니다.


### 예시

입출력 예

|arr|	idx|	result|
|---|---|---|
|[0, 0, 0, 1]	|1|	3|
|[1, 0, 0, 1, 0, 0]	|4	|-1|
|[1, 1, 1, 1, 0]	|3|	3|

입출력 예 #1

1보다 크면서 원소가 1인 가장 작은 인덱스는 3입니다. 따라서 3을 return 합니다.

입출력 예 #2

4번 인덱스 이후에 1은 등장하지 않습니다. 따라서 -1을 return 합니다.

입출력 예 #3

3번 인덱스의 값이 1입니다. 따라서 3을 return 합니다.


## 풀이

```js
function solution(arr, idx) {
    var answer = 0;
    answer = arr.findIndex((num, i) => {
        return num === 1 && i >= idx
    })
    return answer;
}
```
