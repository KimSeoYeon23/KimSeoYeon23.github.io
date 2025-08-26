---
layout: post
title:  "왼쪽 오른쪽"
date:   2025-08-25 20:02:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 왼쪽 오른쪽

### 문제

문자열 리스트 `str_list`에는 "u", "d", "l", "r" 네 개의 문자열이 여러 개 저장되어 있습니다. `str_list`에서 "l"과 "r" 중 먼저 나오는 문자열이 "l"이라면 해당 문자열을 기준으로 왼쪽에 있는 문자열들을 순서대로 담은 리스트를, 먼저 나오는 문자열이 "r"이라면 해당 문자열을 기준으로 오른쪽에 있는 문자열들을 순서대로 담은 리스트를 return하도록 solution 함수를 완성해주세요. "l"이나 "r"이 없다면 빈 리스트를 return합니다.

## 제한 사항

- 1 ≤ `str_list`의 길이 ≤ 20
- `str_list`는 "u", "d", "l", "r" 네 개의 문자열로 이루어져 있습니다.

### 예시

입출력 예 #1

- "r"보다 "l"이 먼저 나왔기 때문에 "l"의 왼쪽에 있는 문자열들을 담은 리스트인 ["u", "u"]를 return합니다.

입출력 예 #2

- "l"의 왼쪽에 문자열이 없기 때문에 빈 리스트를 return합니다.

## 풀이

- JavaScript

```js
function solution(str_list) {
    const leftIndex = str_list.findIndex((i) => i === 'l')
    const rightIndex = str_list.findIndex(i => i === 'r')
    
    if (leftIndex === -1 || rightIndex === -1) {
        if (rightIndex !== -1 && leftIndex === -1) {
            return str_list.slice(rightIndex+1)
        } else if (leftIndex !== -1 && rightIndex === -1) {
            return str_list.slice(0, leftIndex)
        }
        return []
    }
    
    if (leftIndex !== -1 && leftIndex < rightIndex) {
        return str_list.slice(0, leftIndex)
    } else if (rightIndex !== -1 && rightIndex < leftIndex) {
        return str_list.slice(rightIndex+1)
    }
}
```

- 다른 사람 풀이

반복문을 쓸 생각을 못했다,,

```js
function solution(str_list) {
    for (let i=0; i < str_list.length; i++) {
        if (str_list[i] === 'l') return str_list.slice(0, i)
        if (str_list[i] === 'r') return str_list.slice(i+1)
    }
    
    return []
}
```

- python

```python
def solution(str_list):
    for i in range(len(str_list)):
        if str_list[i] == 'l':
            return str_list[0:i]
        elif str_list[i] == 'r':
            return str_list[i+1:]
    return []
```