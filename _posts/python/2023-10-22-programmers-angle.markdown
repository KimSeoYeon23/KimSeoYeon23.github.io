---
layout: post
title:  "프로그래머스 각도기"
date:   2023-10-22 17:47:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 각도기

### 문제

각에서 0도 초과 90도 미만은 예각, 90도는 직각, 90도 초과 180도 미만은 둔각 180도는 평각으로 분류합니다. 각 `angle`이 매개변수로 주어질 때 예각일 때 1, 직각일 때 2, 둔각일 때 3, 평각일 때 4를 return하도록 solution 함수를 완성해주세요.

- 예각: 0 < `angle` < 90
- 직각: `angle` = 90
- 둔각: 90 < `angle` < 180
- 평각: `angle` = 180

### 제한사항

- 0 < `angle` < 180
- `angle`은 정수입니다.

### 입출력 예

| angle | result |
| --- | --- |
| `70` | `1` |
| `91` | `3` |
| `180` | `4` |

### 입출력 예 설명

**입출력 예 #1**

- `angle`이 70이므로 예각입니다. 따라서 1을 return합니다.

**입출력 예 #2**

- `angle`이 91이므로 둔각입니다. 따라서 3을 return합니다.

**입출력 예 #3**

- `angle`이 180이므로 평각입니다. 따라서 4를 return합니다.

### 풀이

```py
def solution(angle):
    if angle < 90:
        return 1
    elif angle == 90:
        return 2
    elif 90 < angle < 180:
        return 3
    else:
        return 4
```