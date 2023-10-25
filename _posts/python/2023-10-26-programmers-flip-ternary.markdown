---
layout: post
title:  "프로그래머스 3진법 뒤집기"
date:   2023-10-26 00:01:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 3진법 뒤집기

### 문제

자연수 `n`이 매개변수로 주어집니다. `n`을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

### 제한사항

- `n`은 1 이상 100,000,000 이하인 자연수입니다.

### 입출력 예

| n | result |
| --- | --- | 
| `45` | `7` |
| `125` | `229` |

### 입출력 예 설명

**입출력 예 #1**

- 답을 도출하는 과정은 다음과 같습니다.

| n(10진법) | n(3진법) | 앞뒤 반전(3진법) | 10진법으로 표현 | 
| --- | --- | --- | --- |
| `45` | `1200` | `0021` | `7` |

- 따라서 7을 return 해야 합니다.

**입출력 예 #2**

- 답을 도출하는 과정은 다음과 같습니다.

| n(10진법) | n(3진법) | 앞뒤 반전(3진법) | 10진법으로 표현 | 
| --- | --- | --- | --- |
| `125` | `11122` | `22111` | `229` |

- 따라서 229를 return 해야 합니다.

### 풀이

```py
def solution(n):
    answer = 0
    rev_base = ''
    while n > 0:
        n, mod = divmod(n, 3)
        rev_base += str(mod)
    return int(rev_base, 3)
```

**n진수 -> 10진수**

> 결과값은 모두 string이다.

python에서는 기본적으로 `int()` 라는 함수를 지원한다.

```py
int(string, base)
```

위와 같은 형식으로 사용하는데, `base`에는 진법을 넣으면 된다.

> 참고: <https://velog.io/@code_angler/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%A7%84%EC%88%98%EB%B3%80%ED%99%982%EC%A7%84%EB%B2%95-3%EC%A7%84%EB%B2%95-5%EC%A7%84%EB%B2%95-10%EC%A7%84%EB%B2%95n%EC%A7%84%EB%B2%95>