---
layout: post
title:  "프로그래머스 직사각형 별찍기"
date:   2023-10-26 00:26:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 직사각형 별찍기

### 문제

이 문제에는 표준 입력으로 두 개의 정수 `n`과 `m`이 주어집니다.  
별(*) 문자를 이용해 가로의 길이가 `n`, 세로의 길이가 `m`인 직사각형 형태를 출력해보세요.

### 제한사항

- `n`과 `m`은 각각 1000 이하인 자연수입니다.

### 예시

**입력**

```text
5 3
```

**출력**

```text
*****
*****
*****
```

### 풀이

```py
a, b = map(int, input().strip().split(' '))

result = ''
for i in range(b):
    result = "*" * a
    print(result)

# or

a, b = map(int, input().strip().split(' '))

for _ in range(b):
    print("*" * a)
```