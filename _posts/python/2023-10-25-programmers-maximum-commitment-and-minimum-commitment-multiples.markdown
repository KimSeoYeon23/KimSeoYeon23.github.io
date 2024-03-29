---
layout: post
title:  "프로그래머스 최대공약수와 최소공배수"
date:   2023-10-25 23:46:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 최대공약수와 최소공배수

### 문제

두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해보세요. 배열의 맨 앞에 최대공약수, 그 다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

### 제한사항

- 두 수는 1이상 1000000이하의 자연수입니다.

### 입출력 예

| n | m | result |
| --- | --- | --- |
| `3` | `12` | `[3, 12]` |
| `2` | `5` | `[1, 10]` |

### 입출력 예 설명

**입출력 예 #1**

- 위의 설명과 같습니다.

**입출력 예 #2**

- 자연수 2와 5의 최대공약수는 1, 최소공배수는 10이므로 [1, 10]을 리턴해야 합니다.

### 풀이

```py
import math

def solution(n, m):
    return [math.gcd(n, m), (n * m) // math.gcd(n, m)]
```

최소공배수를 구하는 `math.lcm()`이라는 함수가 있는데, `lcm()`은 파이썬 3.9버전부터 사용할 수 있고, 3.5 ~ 3.8버전에서는 없다고 뜬다. 그래서 위와 같은 방법으로 최소공배수를 구했다.