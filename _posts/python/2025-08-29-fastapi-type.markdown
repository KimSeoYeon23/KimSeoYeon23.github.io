---
layout: post
title: "FastAPI 타입"
date: 2025-08-29 10:11:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 타입

## 파이썬 타입

파이썬은 선택적으로 "타입 힌트(type hints)"를 지원한다.
이러한 **타입 힌트**들은 변수의 타입을 선언할 수 있게 해주는 특수한 구문이다.

**FastAPI**는 타입 힌트에 기반을 두고 있으며, 이는 많은 장점과 이익이 있다.


## 동기 부여

```python
def get_full_name(first_name, last_name):
	full_name: first_name.title() + " " + last_name.title()
	return full_name
	
print(get_full_name("john", "doe"))
```

이 프로그램을 실행한 결과값
```text
John Doe
```

함수는 아래와 같이 실행된다.

- `first_name`과 `last_name`을 받는다.
- `title()`로 각 첫 문자를 대문자로 변환시킨다.
- 두 단어를 중간에 공백을 두고 연결한다.


### 타입 추가하기

위의 코드에서 한 줄만 수정해본다.

```python
first_name, last_name
```

을 아래와 같이 바꾼다.

```python
first_name: str, last_name: str
```

이게 "타입 힌트" 이다.

```python
def get_full_name(first_name: str, last_name: str):
	full_name: first_name.title() + " " + last_name.title()
	return full_name
	
print(get_full_name("john", "doe"))
```

타입 힌트는 다음과 같이 기본 값을 선언하는 것과는 다르다.

```python
first_name="john", last_name="doe"
```

이는 다른 것이다.

등호(`=`) 대신 콜론(`:`)을 쓰고 있다. 일반적으로 타입 힌트를 추가한다고 해서 특별하게 어떤 일이 일어나지도 않는다. 


## 타입 선언

### Simple 타입

`str` 뿐 아니라 모든 파이썬 표준 타입을 선언할 수 있다.

예를 들면

- `int`
- `float`
- `bool`
- `bytes`

```python
def get_time(item_a: str, item_b: int, item_c: float, item_d: bool, item_e: bytes):
	return item_a, item_b, item_c, item_d, item_e
```



### 타입 매개변수를 활용한 Generic(제네릭) 타입

`dict`, `list`, `set`, `tuple` 과 같은 값을 저장할 수 있는 데이터 구조가 있고, 내부의 값은 각자의 타입을 가질 수도 있다. 타입과 내부 타입을 선언하기 위해서는 파이썬 표준 모듈인 `typing`을 이용해야 한다.

구체적으로는 아래 타입 힌트를 지원한다.

**`List`**

예를 들면, `str`의 `list`인 변수를 정의해본다. `typing`에서 `List`(대문자 `L`)를 import 한다.

```python
from typing import List

def process_items(items: List[str]):
	for item in items:
		print(item)
```


- python 3.9 버전부터
```python
def process_items(items: list[str]):
	for item in items:
		print(item)
```

콜론(`:`) 문법을 이용하여 변수를 선언한다. 타입으로는 `List`를 넣어준다.
이 때 배열은 내부 타입을 포함하는 타입이기 때문에 대괄호 안에 넣어준다.

이는 "`items`은 `list`인데, 배열에 들어있는 아이템 각각은 `str`이다" 라는 뜻이다.

`tuple`과 `set`도 동일하게 선언할 수 있다.

```python
from typing import Set, Tuple

def process_items(items_t: Tuple[int, int, str], items_s: Set[bytes]):
	return items_t, items_s
```

- python 3.9 버전부터
```python
def process_items(items_t: tuple[int, int, str], items_s: set[bytes]):
	return items_t, items_s
```

이 뜻은 아래와 같다

- 변수 `items_t`는 차례대로 `int`, `int`, `str`인 `tuple` 이다.
- 변수 `items_s`는 각 아이템이 `bytes`인 `set`이다.


`dict`를 선언하려면 컴마로 구분된 2개의 파라미터가 필요하다.
첫 번째 매개변수는 `dict`의 키(key)이고, 두 번째 매개변수는 `dict`의 값(value)이다.

```python
from typing import Dict

def process_items(prices: Dict[str, float]):
	for item_name, item_price in prices.items():
		print(item_name)
		print(item_price)
```


- python 3.9 버전부터
```python
def process_items(prices: dict[str, float]):
	for item_name, item_price in prices.items():
		print(item_name)
		print(item_price)
```

이 뜻은 아래와 같다.

- 변수 `prices`는 `dict`이다.
	- `dict`의 키(key)는 `str` 타입이다. (각 아이템의 이름(name))
	- `dict`의 값(value)는 `float` 타입이다. (각 아이템의 가격(price))


`str`과 같이 타입을 선언할 때 `Optional`을 쓸 수도 있는데, "선택적(Optional)"이기 때문에 `None`도 될 수 있다.

```python
from typing import Optional

def say_hi(name: Optional[str] = None):
	if name is not None:
		print(f"Hey {name}!")
	else:
		print("Hello World")
```

`Optional[str]`을 `str` 대신 쓰게 되면, 특정 값이 실제로는 `None`이 될 수도 있는데 항상 `str`이라고 가정하는 상황에서 에디터가 에러를 찾게 도와줄 수 있다.


### Generic(제네릭) 타입

이 타입은 대괄호 안에 매개변수를 가지며, 종류는:

- `List`
- `Tuple`
- `Set`
- `Dict`
- `Optional`
- ...등등

위와 같은 타입은 **Generic(제네릭) 타입** 혹은 **Generics(제네릭스)**라고 불린다.



## 타입으로서의 클래스

변수의 타입으로 클래스를 선언할 수도 있다. 

이름(name)을 가진 `Person` 클래스가 있다고 해본다.

```python
class Person:
	def __init__(self, name: str):
		self.name = name

def get_person_name(one_person: Person):
	return on_person.name
```

그렇게 하면 변수를 `Person`이라고 선언할 수 있게 된다.


## Pydantic 모델

Pydantic은 데이터 검증(Validation)을 위한 파이썬 라이브러리이다.
속성을 포함한 클래스 형태로 "모양(shape)"을 선언할 수 있다. 그리고 각 속성은 타입을 가지고 있다.

이 클래스를 활용해서 값을 가지고 있는 인스턴스를 만들게 되면, 필요한 경우에는 적당한 타입으로 변환까지 시키기도 해서 데이터가 포함된 객체를 반환한다.

그리고 결과 객체에 대해서는 데이터의 도움을 받을 수 있게 된다.

Pydantic 공식 문서 예시

```python
from datetime import datetime
from typing import List, Union

from pydantic import BaseModel


class User(BaseModel):
    id: int
    name: str = "John Doe"
    signup_ts: Union[datetime, None] = None
    friends: List[int] = []


external_data = {
    "id": "123",
    "signup_ts": "2017-06-01 12:22",
    "friends": [1, "2", b"3"],
}
user = User(**external_data)
print(user)
# > User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
# > 123
```


- Python 3.9버전 부터
```python
from datetime import datetime
from typing import Union

from pydantic import BaseModel


class User(BaseModel):
    id: int
    name: str = "John Doe"
    signup_ts: Union[datetime, None] = None
    friends: list[int] = []


external_data = {
    "id": "123",
    "signup_ts": "2017-06-01 12:22",
    "friends": [1, "2", b"3"],
}
user = User(**external_data)
print(user)
# > User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
# > 123
```


- Python 3.10 버전 부터
```python
from datetime import datetime

from pydantic import BaseModel


class User(BaseModel):
    id: int
    name: str = "John Doe"
    signup_ts: datetime | None = None
    friends: list[int] = []


external_data = {
    "id": "123",
    "signup_ts": "2017-06-01 12:22",
    "friends": [1, "2", b"3"],
}
user = User(**external_data)
print(user)
# > User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
# > 123
```




## FastAPI에서의 타입 힌트

FastAPI는 여러 부분에서 타입 힌트의 장점을 취하고 있다.
**FastAPI**에서 타입 힌트와 함께 매개변수를 선언하면 장점은:

- **에디터 도움**.
- **타입 확인**.
- 
FastAPI는 같은 정의를 아래에도 적용한다.

- **요구사항 정의**: 요청 경로 매개변수, 쿼리 매개변수, 헤더, 바디, 의존성 등
- **데이터 변환**: 요청에서 요구한 타입으로
- **데이터 검증**
	- 각 요청마다
		- 데이터가 유효하지 않은 경우에는 **자동으로 에러**를 발생한다.
- OpenAPI를 활용한 API 문서화
	- 자동으로 상호작용하는 유저 인터페이스에 쓰이게 된다.


> 출처: [https://fastapi.tiangolo.com/ko/python-types/](https://fastapi.tiangolo.com/ko/python-types/)