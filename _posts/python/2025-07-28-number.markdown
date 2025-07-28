---
layout: post
title: "조건문"
date: 2025-07-25 15:41:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

# 조건문이란 무엇인가?

if 조건문에서 ‘조건문’이란 참과 거짓을 판단하는 문장을 말한다.

  

## 비교 연산자

|   |   |
|---|---|
|**비교연산자**|**설명**|
|x < y|x가 y보다 작다.|
|x > y|x가 y보다 크다.|
|x == y|x와 y가 같다.|
|x ≠ y|x와 y가 같지 않다.|
|x ≥ y|x가 y보다 크거나 같다.|
|x ≤ y|x가 y보다 작거나 같다.|

이제 이 연산자를 어떻게 사용하는지 알아 본다.

```Python
>>> x = 3
>>> y = 2
>>> x > y
True
```

x에 3, y에 2를 대입한 후 `x > y`라는 조건문을 수행하면 True를 리턴한다. `x > y` 조건문이 참이기 때문이다.

```Python
>>> x < y
False
```

위 조건문은 거짓이기 때문에 False를 리턴한다.

```Python
>>> x == y
False
```

x와 y는 같지 않다. 따라서 위 조건문은 거짓이므로 False를 리턴한다.

```Python
>>> x != y
True
```

x와 y는 같지 않다. 따라서 위 조건문은 참이므로 True를 리턴한다.

  

## and, or, not

조건을 판단하기 위해 사용하는 다른 연산자로는 and, or, not이 있다. 각각의 연산자는 다음처럼 동작한다.

|   |   |
|---|---|
|**연산자**|**설명**|
|x or y|x와 y 둘 중 하나만 참이어도 참이다.|
|x and y|x와 y 모두 참이어야 참이다.|
|not x|x가 거짓이면 참이다.|

다음 예를 통해 or 연산자의 사용법을 알아본다.

```Python
돈이 3000원 이상 있거나 카드가 있다면 택시를 타고 가고, 그렇지 않으면 걸어가라.
```

```Python
>>> money = 2000
>>> card = True
>>> if money >= 3000 or card:
...     print("택시를 타고 가라")
... else:
...     print("걸어가라")
...
택시를 타고 가라
```

money는 2000이지만, card가 True이기 때문에 `money >= 3000 or card` 조건문이 참이 된다. 따라서 if 문에 속한 ‘택시를 타고 가라’ 문장이 출력된다.

  

## in, not in

파이썬은 다른 프로그래밍 언어에서 쉽게 볼 수 없는 조건문도 제공한다. 바로 다음과 같은 것들이다.

|   |   |
|---|---|
|**in**|**not in**|
|x in 리스트|x not in 리스트|
|x in 튜플|x not in 튜플|
|x in 문자열|x not in 문자열|

영어 단어 in의 뜻이 ‘~안에’라는 것을 생각해 보면 다음 예가 쉽게 이해될 것이다.

```Python
>>> 1 in [1, 2, 3]
True
>>> 1 not in [1, 2, 3]
False
```

앞에서 첫 번째 예는 ‘[1, 2, 3]이라는 리스트 안에 1이 있는가?’라는 조건문이다. 1은 [1, 2, 3] 안에 있으므로 참이 되어 True를 리턴한다. 두 번째 예는 ‘[1, 2, 3] 리스트 안에 1이 없는가?’라는 조건문이다. 1은 [1, 2, 3] 안에 있으므로 거짓이 되어 False를 리턴한다.

다음은 튜플과 문자열에 in과 not in을 적용한 예이다. 각각의 결과가 나온 이유는 쉽게 유추할 수 있다.

```Python
>>> 'a' in ('a', 'b', 'c')
True
>>> 'j' not in 'python'
True
```

이번에는 다른 예제에 in을 적용해 본다.

```Python
만약 주머니에 돈이 있으면 택시를 타고 가고, 없으면 걸어가라.
```

```Python
>>> pocket = ['paper', 'cellphone', 'money']
>>> if 'money' in pocket:
...     print("택시를 타고 가라")
... else:
...     print("걸어가라")
...
택시를 타고 가라
```

`['paper', 'cellphone', 'money']` 리스트 안에 ‘money’가 있으므로 `'money' in pocket'`은 참이 된다. 따라서 if 문에 속한 문장이 수행된다.

  

- **조건문에서 아무 일도 하지 않게 설정하고 싶다면?**
    
    가끔 조건문의 참, 거짓에 따라 실행할 행동을 정의할 때나 아무런 일도 하지 않도록 설정하고 싶을 때가 있다.
    
    ```Python
    주머니에 돈이 있으면 가만히 있고, 주머니에 돈이 없으면 카드를 꺼내라.
    ```
    
    이럴 때 사용하는 것이 바로 pass이다. 위 예를 pass를 적용해서 구현해 보자.
    
    ```Python
    >>> pocket = ['paper', 'cellphone', 'money']
    >>> if 'money' in pocket:
    ...     pass
    ... else:
    ...     print("카드를 꺼내라")
    ...
    ```
    
    pocket 리스트 안에 money 문자열이 있기 때문에 if 문 다음 문장인 pass가 수행되고 아무런 결괏값도 보여 주지 않는다.
    
      
    

  

# 조건부 표현식

score가 60 이상일 경우 message에 문자열 ‘success’, 아닐 경우에는 문자열 ‘failure’를 대입하는 코드이다.

```Python
if score >= 60:
	message = 'success'
else:
	message = 'failure'
```

파이썬의 조건부 표현식(conditional expression)을 사용하면 위 코드를 다음과 같이 간단히 표현할 수 있다.

```Python
message = 'success' if score >= 60 else 'failure'
```

조건부 표현식은 다음과 같이 정의한다.

```Python
변수 = 조건문이_참인_경우의_값 if 조건문 else 조건문이_거짓인_경우의_값
```

조건부 표현식은 가독성에 유리하고 한 줄로 작성할 수 있어 활용성이 좋다.

  

> 출처: [https://wikidocs.net/20](https://wikidocs.net/20)