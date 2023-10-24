---
layout: post
title:  "프로그래머스 아이스 아메리카노"
date:   2023-10-24 20:17:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 아이스 아메리카노

### 문제

머쓱이는 추운 날에도 아이스 아메리카노만 마십니다. 아이스 아메리카노는 한잔에 5,500원입니다. 머쓱이가 가지고 있는 돈 `money`가 매개변수로 주어질 때, 머쓱이가 최대로 마실 수 있는 아메리카노의 잔 수와 남는 돈을 순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.

### 제한사항

- 0 < `money` <= 1,000,000

### 입출력 예

| money | result |
| --- | --- |
| `5,500` | `[1, 0]` |
| `15,000` | `[2, 4000]` |

### 입출력 예 설명

**입출력 예 #1**

- 5,500원은 아이스 아메리카노 한 잔을 살 수 있고 잔돈은 0원입니다.

**입출력 예 #2**

- 15,000원은 아이스 아메리카노 두 잔을 살 수 있고 잔돈은 4,000원입니다.

### 풀이

```py
def solution(money):
	price = 5500
	return [money // price, money % price]

# or

def solution(money):
    return divmod(money, 5500)
```