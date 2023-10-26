---
layout: post
title:  "프로그래머스 시저 암호"
date:   2023-10-26 20:54:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 프로그래머스 코딩테스트 시저 암호

### 문제

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다 예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 `s`와 거리 `n`을 입력받아 `s`를 `n`만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

### 제한사항

- 공백은 아무리 밀어도 공백입니다.
- `s`는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
- `s`의 길이는 8000이하입니다.
- `n`은 1 이상, 25이항니 자연수입니다.

### 입출력 예

| s | n | result |
| --- | --- | --- |
| `"AB"` | `1` | `"BC"` |
| `"z"` | `1` | `"a"` |
| `"a B z"` | `4` | `"e F d"` |

### 풀이

```py
def solution(s, n):
    answer = []
    for char in s:
        if char.isalpha():
            start = ord('A') if char.isupper() else ord('a')
            answer.append(chr((ord(char) - start + n) % 26 + start))
        else:
            answer.append(char)
    return ''.join(answer)
```

1. 먼저 빈 리스트를 생성하여 암호화된 문자들을 저장한다.
2. 문자열 `s`의 각 문자 `char`에 대해 반복한다.
3. `if char.isalpha()` 이 조건문은 `char`가 알파벳 문자인지 확인한다.
   1. `isalpha()` 함수는 문자가 알파벳이면 `True`를, 아니면 `False`를 반환한다.
4. `start = ord('A') if char.isupper() else ord('a')` 이 부분은 `char`가 대문자인지 소문자인지에 따라 시작점을 정한다.
   1. `isupper()` 함수는 문자가 대문자이면 `True`를, 아니면 `False`를 반환한다.
   2. `ord('A')`는 대문자 'A'의 아스키 코드 값을 반환한다.
   3. `ord('a')`는 소문자 'a'의 아스키 코드 값을 반환한다.
5. `answer.append(chr((ord(char) - start + n) % 26 + start))` 이 부분은 `char`를 `n`만큼 시저 암호 방식으로 암호화한다.
   1. `ord(char)`는 `char`의 아스키 코드 값을 반환한다.
   2. `ord(char) - start`는 `char`를 0부터 시작하는 알파벳 인덱스로 변환한다.
   3. `(ord(char) - start + n) % 26`는 `char`를 `n`만큼 오른쪽으로 밀어서 암호화하고, 26으로 나눈 나머지를 구한다.
   4. `chr((ord(char) - start + n) % 26 + start)`는 암호화된 인덱스를 다시 문자로 변환한다.
6. `else:` 이 부분은 `char`가 알파벳이 아닌 경우이다.
   1. 알파벳이 아닌 문자는 암호화하지 않고 그대로 `answer`에 추가한다.
7. 마지막으로 `''.join(answer)`는 `answer` 리스트의 문자들을 연결하여 문자열로 변환한다.