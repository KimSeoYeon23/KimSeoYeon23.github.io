---
layout: post
title:  "이차원 배열 대각선 순회하기"
date:   2025-08-27 12:05:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 이차원 배열 대각선 순회하기

### 문제

2차원 정수 배열 `board`와 정수 `k`가 주어집니다.

`i` + `j` <= `k`를 만족하는 모든 (`i`, `j`)에 대한 `board[i][j]`의 합을 return 하는 solution 함수를 완성해 주세요.

## 제한 사항

1 ≤ `board`의 길이 ≤ 100
1 ≤ `board[i]`의 길이 ≤ 100
1 ≤ ``board[i]`[j]` ≤ 10,000
모든 `board[i]`의 길이는 같습니다.
0 ≤ `k` < `board`의 길이 + `board[i]`의 길이

### 예시

입출력 예 #1

- 입출력 예 #1의 board를 표로 나타내면 다음과 같습니다.

|i \ j|	0|	1|	2|
|---|---|---|---|
|0|	0|	1|	2|
|1|	1|	2|	3|
|2|	2|	3|	4|
|3|	3|	4|	5|

- `i` + `j`가 2보다 작거나 같은 항들의 합은 0 + 1 + 2 + 1 + 2 + 2 = 8이므로 8을 return 합니다.

## 풀이

- JavaScript

```js
function solution(board, k) {
    var answer = 0;
    
    for (let i = 0; i < board.length; i++) {
        for (let j = 0; j < board[i].length; j++) {
            if (i+j <= k) {
                answer += board[i][j]
            }
        }
    }
    
    
    return answer;
}
```


- python

```python
def solution(board, k):
    answer = 0
    
    for i, one in enumerate(board):
        for j, two in enumerate(one):
            if i+j <= k:
                answer += two
                
    return answer
```