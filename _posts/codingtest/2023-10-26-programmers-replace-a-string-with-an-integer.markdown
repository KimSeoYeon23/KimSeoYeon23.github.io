---
layout: post
title:  "프로그래머스 문자열을 정수로 바꾸기"
date:   2023-10-26 00:12:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 문자열을 정수로 바꾸기

### 문제

문자열 `s`를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

### 제한사항

- `s`의 길이는 1 이상 5이하입니다.
- `s`의 맨 앞에는 부호(+, -)가 올 수 있습니다.
- `s`는 부호와 숫자로만 이루어져있습니다.
- `s`는 "0"으로 시작하지 않습니다.

### 입출력 예

예를 들어 str이 "1234"이면 1234를 반환하고, "-1234"이면 -1234를 반환하면 됩니다.  
str은 부호(+, -)와 숫자로만 구성되어 있고, 잘못된 값이 입력되는 경우는 없습니다.

### 풀이

```py
def solution(s):
    return int(s)
```