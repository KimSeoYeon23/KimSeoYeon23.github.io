---
layout: post
title:  "글자 지우기"
date:   2025-08-18 18:30:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 글자 지우기

### 문제

문자열 `my_string`과 정수 배열 `indices`가 주어질 때, `my_string`에서 `indices`의 원소에 해당하는 인덱스의 글자를 지우고 이어 붙인 문자열을 return 하는 solution 함수를 작성해 주세요.

## 제한 사항

- 1 ≤ `indices`의 길이 < `my_string`의 길이 ≤ 100
- `my_string`은 영소문자로만 이루어져 있습니다
- 0 ≤ `indices`의 원소 < `my_string`의 길이
- `indices`의 원소는 모두 서로 다릅니다.


### 예시

입출력 예 #1

예제 1번의 my_string의 인덱스가 잘 보이도록 표를 만들면 다음과 같습니다.

|index|	0|	1|	2|	3|	4|	5|	6|	7|	8|	9|	10|	11|	12|	13|	14|	15|	16|	17|	18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|my_string|	a|	p|	p|	o|	r|	o|	o|	g|	r|	a|	p|	e|	m|	m|	e|	m|	p|	r|	s|

`indices`에 있는 인덱스의 글자들을 지우고 이어붙이면 "programmers"가 되므로 이를 return 합니다.


## 풀이

```js
function solution(my_string, indices) {
    var answer = '';
    
    for(let i = 0; i<my_string.length; i++){
        if(!indices.includes(i)){
            answer += my_string[i]
        }
    }
    return answer;
}
```
