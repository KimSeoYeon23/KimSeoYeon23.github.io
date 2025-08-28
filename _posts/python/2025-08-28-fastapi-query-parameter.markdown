---
layout: post
title: "FastAPI 쿼리 매개변수"
date: 2025-08-28 09:35:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 경로 매개변수

## 쿼리 매개변수

경로 매개변수의 일부가 아닌 다른 함수 매개변수를 선언하면 "쿼리" 매개변수로 자동 해석한다.

```python
from fastapi impot FastAPI

app = FastAPI()

fake_items_db = [{"item_name": "Foo"}, {"item_name": "Bar"}, {"item_name": "Baz"}]

@app.get("/items")
async def read_item(skip: int = 0, limit: int = 10):
	return fake_items_db[skip : skip + limit]
```

쿼리는 URL에서 `?` 후에 나오고 `&` 으로 구분되는 키-값 쌍의 집합이다.

예를 들어, 아래 URL에서:

```text
http://127.0.0.1:8000/items/?skip=0&limit=10
```

쿼리 매개변수는:

- `skip`: 값 `0`을 가진다.
- `limit`: 값 `10`을 가진다.

URL의 일부이므로 "자연스럽게" 문자열이다. 하지만 파이썬 타입과 함께 선언할 경우(위 예에서 `int`), 해당 타입으로 변환 및 검증된다.

경로 매개변수에 적용된 동일한 프로세스가 쿼리 매개변수에도 적용된다.

- 편집기 지원
- 데이터 파싱
- 데이터 검증
- 자동 문서화


## 기본값

쿼리 매개변수는 경로에서 고정된 부분이 아니기 때문에 선택적일 수 있고 기본값을 가질 수 있다.
위 예에서 `skip = 0`과 `limit = 10`은 기본값을 갖고 있다.

그러므로 URL로 이동하는 것은:

```text
http://127.0.0.1:8000/items/
```

아래로 이동하는 것과 같다.

```text
http://127.0.0.1:8000/items/?skip=0&limit=10
```

하지만 가령 아래로 이동된 경우:

```text
http://127.0.0.1:8000/items/?skip=20
```

함수의 매개변수 값은 아래가 된다.
- `skip=20`: URL에서 지정했기 때문이다
- `limit=10`: 기본값이기 때문이다.


## 선택적 매개변수

같은 방법으로 기본값을 `None`으로 설정하여 선택적 매개변수를 선언할 수 있다.

```python
from typing import Union
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_item(item_id: str, q: Union[str, None] = None):
	if q:
		return {"item_id": item_id, "q": q}
	return {"item_id": item_id}
```


- Python 3.10 버전부터
```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/{item_id}")
async def read_item(item_id: str, q: str | None = None):
    if q:
        return {"item_id": item_id, "q": q}
    return {"item_id": item_id}
```


이 경우 함수 매개변수 `q`는 선택적이며 기본값으로 `None` 값이 된다.


## 쿼리 매개변수 형변환

`bool` 형으로 선언할 수도 있고, 아래처럼 변환된다.

```python
from typing import Union
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_item(item_id: str, q: Union[str, None] = None, short: bool = False):
	item = {"item_id": item_id}
	if q:
		return {{"q": q}}
	if not short:
		item.update(
			{"description": "This is an amazing item that ahs a long description"}
		)
	return item
```

- Python 3.10 버전부터
```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/{item_id}")
async def read_item(item_id: str, q: str | None = None, short: bool = False):
    item = {"item_id": item_id}
    if q:
        item.update({"q": q})
    if not short:
        item.update(
            {"description": "This is an amazing item that has a long description"}
        )
    return item
```

이 경우, 아래로 이동하면:
```text
http://127.0.0.1:8000/items/foo?short=1
or
http://127.0.0.1:8000/items/foo?short=True
or
http://127.0.0.1:8000/items/foo?short=true
or
http://127.0.0.1:8000/items/foo?short=on
or
http://127.0.0.1:8000/items/foo?short=yes
```

또는 다른 어떤 변형(대문자, 첫 글자만 대문자 등)이더라도 함수는 매개변수 `bool`을 가진 `short`의 값이 `True`임을 안다. 그렇지 않은 경우 `False`이다.



## 여러 경로/쿼리 매개변수

여러 경로 매개변수와 쿼리 매개변수를 동시에 선언할 수 있으며 **FastAPI**는 어느 것이 무엇인지 알고 있다. 그리고 특정 순서로 선언할 필요가 없다. 매개변수들은 이름으로 감지된다.

```python
from typing import Union
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/{user_id}/items/{item_id}")
async def read_user_item(user_id: int, item_id: str, q: Union[str, None] = None, short: bool = False):
	item = {"item_id": item_id, "owner_id": user_id}
	if q:
		item.update({"q": q})
	if not short:
		item.update(
			{"description": "this is an amazing item that has a long description"}
		)
	return item
```

- Python 3.10 부터
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/{user_id}/items/{item_id}")
async def read_user_item(user_id: int, item_id: str, q: str | None = None, short: bool = False):
    item = {"item_id": item_id, "owner_id": user_id}
    if q:
        item.update({"q": q})
    if not short:
        item.update(
            {"description": "This is an amazing item that has a long description"}
        )
    return item
```



## 필수 쿼리 매개변수

경로가 아닌 매개변수에 대한 기본값을 선언할 때, 해당 매개변수는 필수적(Required)이지 않았다. 

특정 값을 추가하지 않고 선택적으로 만들기 위해선 기본값을 `None`으로 설정하면 된다. 그러나 쿼리 매개변수를 필수로 만들려면 단순히 기본값을 선언하지 않으면 된다.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_user_item(item_id: str, needy: str):
	item = {"item_id": item_id, "needy": needy}
	return item
```

여기 쿼리 매개변수 `needy`는 `str` 형인 필수 쿼리 매개변수이다.
브라우저에서 아래와 같은 URL을 연다면

```text
http://127.0.0.1:8000/items/foo-item
```

필수 매개변수 `needy`를 넣지 않았기 때문에 아래와 같은 오류를 보게 된다.

```json
{
    "detail": [
        {
            "loc": [
                "query",
                "needy"
            ],
            "msg": "field required",
            "type": "value_error.missing"
        }
    ]
}
```

`needy`는 필수 매개변수이므로 URL에 반드시 설정해줘야 한다.

```text
http://127.0.0.1:8000/items/foo-item?needy=sooooneedy
```

아래처럼 작동한다.

```json
{
	"item_id": "foo-item",
	"needy": "sooooneedy"
}
```

그리고 물론, 일부 매개변수는 필수로, 다른 일부는 기본값을, 또 다른 일부는 선택적으로 선언할 수 있다.

```python
from typing import Union
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_user_item(item_id: str, needy: str, skip: int = 0, limit: Union[int, None] = None):
	item = {"item_id": item_id, "needy": needy, "skip": skip, "limit": limit}
	return item
```

- Python 3.10 부터
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_user_item(item_id: str, needy: str, skip: int = 0, limit: int | None = None):
	item = {"item_id": item_id, "needy": needy, "skip": skip, "limit": limit}
	return item
```

위 예시에서는 3가지 쿼리 매개변수가 있다.

- `needy`, 필수적인 `str`
- `skip`, 기본값이 `0`인 `int`
- `limit`, 선택적인 `int`


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/query-params/](https://fastapi.tiangolo.com/ko/tutorial/query-params/)