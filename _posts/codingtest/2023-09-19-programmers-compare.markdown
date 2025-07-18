---
layout: post
title:  "프로그래머스 숫자 비교하기"
date:   2023-09-19 21:05:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 숫자 비교하기

### 문제

정수 `num1`, `num2`가 매개변수로 주어집니다. 두 수가 같으면 1 다르면 -1을 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- 0 <= `num1` <= 10,000
- 0 <= `num2` <= 10,000

### 입출력 예

| num1 | num2 |	result |
| --- | --- | --- |
| `2` | `3` |	`-1` |
| `11` | `11` |	`1` |
| `7` | `99` |	`-1` |

### 입출력 예 설명

**입출력 예 #1**
- `num1`이 2이고 `num2`가 2이므로 다릅니다. 따라서 -1을 return합니다.

**입출력 예 #2**
- `num1`이 11이고 `num2`가 11이므로 같습니다. 따라서 1을 return합니다.

**입출력 예 #3**
- `num1`이 7이고 `num2`가 99이므로 같습니다. 따라서 -1을 return합니다.

### 풀이

```py
def solution(num1, num2):
    if num1 == num2:
        return 1
    else:
        return -1
```