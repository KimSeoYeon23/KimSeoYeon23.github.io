---
layout: post
title:  "문자 개수 세기"
date:   2025-08-18 18:30:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 문자 개수 세기

### 문제

알파벳 대소문자로만 이루어진 문자열 `my_string`이 주어질 때, `my_string`에서 'A'의 개수, `my_string`에서 'B'의 개수,..., `my_string`에서 'Z'의 개수, `my_string`에서 'a'의 개수, `my_string`에서 'b'의 개수,..., `my_string`에서 'z'의 개수를 순서대로 담은 길이 52의 정수 배열을 return 하는 solution 함수를 작성해 주세요.

## 제한 사항

- 1 ≤ `my_string`의 길이 ≤ 1,000


### 예시

입출력 예 #1

예제 1번의 `my_string`에서 'P'가 1개, 'a'가 1개, 'e'가 1개, 'g'가 1개, 'm'이 2개, 'o'가 1개, 'r'가 3개, 's'가 1개 있으므로 [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 2, 0, 1, 0, 0, 3, 1, 0, 0, 0, 0, 0, 0, 0]를 return 합니다.


## 풀이

```js
function solution(my_string) {
    var answer = [];
    const alphabets = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
    
    for (let i = 0; i < alphabets.length; i++) {
        const count = my_string.split(alphabets[i]).length - 1;
        answer.push(count);
    }
    
    return answer;
}
```
