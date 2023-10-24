---
layout: post
title:  "프로그래머스 문자열 뒤집기"
date:   2023-10-24 20:43:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 문자열 뒤집기

### 문제

문자열 `my_string`이 매개변수로 주어집니다. `my_string`을 거꾸로 뒤집은 문자열을 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 1 <= `my_string`의 길이 <= 1,000

### 입출력 예

| my_string | result |
| --- | --- |
| `"jaron"` | `"noraj"` |
| `"bread"` | `"daerb"` |

### 입출력 예 설명

**입출력 예 #1**

- `my_string`이 "jaron"이므로 거꾸로 뒤집은 "noraj"를 return합니다.

**입출력 예 #2**

- `my_string`이 "bread"이므로 거꾸로 뒤집은 "daerb"를 return합니다.

### 풀이

```py
def solution(my_string):
	return my_string[::-1]
```