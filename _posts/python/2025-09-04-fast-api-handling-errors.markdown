---
layout: post
title: "FastAPI Handling Errors"
date: 2025-09-04 10:54:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 Handling Errors

## Handling Errors

API를 사용하는 클라이언트에게 오류를 알려야 하는 상황은 많다. 이 클라이언트는 프론트엔드가 있는 브라우저, 다른 사람의 코드,  IoT 장치 등일 수 있다. 

고객에게 다음 내용을 알려야 할 수도 있다.

- 클라이언트에게 해당 작업을 수행할 수 있는 권한이 없습니다.
- 클라이언트는 해당 리소스에 접근할 수 없습니다.
- 클라이언트가 액세스하려고 했던 항목이 존재하지 않습니다.


이러한 경우에는 일반적으로 400(400 ~ 499) 범위의 HTTP 상태 코드를 반환한다. 이는 200 HTTP 상태 코드(200 ~ 299)와 유사하다. "200" 상태 코드는 요청이 "성공" 했음을 의미한다. 400 범위의 상태 코드는 클라이언트에 오류가 발생했음을 의미한다.


## Use `HTTPException`

오류가 포함된 HTTP 응답을 클라이언트에 반환하려면 `HTTPException` 사용한다.

### Import `HTTPException`

```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

@app.get("/items/{item_id}")
async def read_time(item_id: str):
	if item_id not in items:
		raise HTTPException(status_code=404, detail="Item not found")
	return {"item": items[item_id]}
```


### 코드에서 HTTPException 발생하기

HTTPException은 API와 관련된 추가 데이터가 포함된 일반 Python 예외이다. Python 예외이므로 반환하지 않고 발생시킨다.

이는 경로 작업 함수 내에서 호출하는 유틸리티 함수 내부에서 `HTTPException` 을 발생시키는 경우 경로 작업 함수의 나머지 코드가 실행되지 않고 요청이 즉시 종료되고 `HTTPException`에서 HTTP 오류가 클라이언트로 전송된다는 것을 의미한다.

이 예에서 클라이언트가 존재하지 않는 ID로 항목을 요청하면 `404` 상태 코드로 예외가 발생한다.

```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

@app.get("/items/{item_id}")
async def read_time(item_id: str):
	if item_id not in items:
		raise HTTPException(status_code=404, detail="Item not found")
	return {"item": items[item_id]}
```


### 결과 응답


클라이언트가 `http://example.com/items/foo`(`item_id: foo`)요청하는 경우 해당 클라이언트는 HTTP 상태 코드 200과 다음과 같은 JSON 응답을 받게 된다.

```json
{
	"item": "The Foo Wrestlers"
}
```

하지만 클라이언트가 `http://exaple.com/items/bar` (존재하지 않는 `item_id: bar`)를 요청하면 해당 클라이언트는 HTTP 상태 코드 404("찾을 수 없음" 오류)와 다음과 같은 JSON 응답을 받게 된다.

```json
{
	"detail": "Item not found"
}
```


> `HTTPException`을 발생시킬 때 `str` 뿐만 아니라 JSON으로 변환할 수 있는 모든 값을 `detail` 매개변수로 전달할 수 있다.
> `dict`, `list` 등을 전달할 수 있다.
> 이는 FastAPI에서 자동으로 처리되고 JSON으로 변환된다.


## 사용자 정의 헤더 추가

HTTP 오류에서 사용자 지정 헤더를 추가하는 것이 유용한 몇 가지 상황이 있다. 예를 들어, 특정 유형의 보안이 있다. 아마도 코드에서 직접 사용할 필요는 없을 것이다. 하지만 고급 시나리오에 필요한 경우 사용자 정의 헤더를 추가할 수 있다.


```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

items = {"foo": "The Foo Wrestlers"}

@app.get("/items-header/{item_id}")
async def read_item_header(item_id: str):
	if item_id not in items:
		raise HTTPException(
			status_code=404, 
			detail="Item not found",
			 headers={"X-Error": "There goes my error"}
		 )
	return {"item": items[item_id]}
```



## 사용자 정의 예외 처리기 설치

Starlette의 동일한 예외 유틸리티를 사용하여 사용자 정의 예외 처리기를 추가할 수 있다.

사용자 정의 예외 `UnicornException`이 있다고 가정해 보겠다.(또는 사용자가 사용하는 라이브러리에서 `raise`할 수 있는 예외) 그리고 FastAPI를 사용하여 이 예외를 전역적으로 처리하려고 한다.

`@app.exception_handler()` 사용하여 사용자 정의 예외 처리기를 추가할 수 있다.

```python
from fastapi import FastAPI, Request
from fastapi.response import JSONResponse

class UnicornException(Exception):
	def __init__(self, name: str):
		self.name = name
		
app = FastApI()

@app.exception_handler(UnicornException):
async def unicorn_exception_handler(request: Request, exc: UnicornException):
	return JSONResponse(
		status_code=418,
		content={"message": f"Oops! {exc.name} did something. There goes a rainbow..."},
	)

@app.get("/unicorn/{name}")
async def read_unicorn(name: str):
	if name == "yolo":
		raise UnicornException(name=name)
	return {"unicorn_name": name}
```

여기서 `/unicorn/yolo` 요청하면 경로 작업에서 `UnicornException`이 발생한다. 하지만 이 문제는 `unicorn_exception_handler`에 의해 처리된다. 따라서 HTTP 상태 코드 `418`과 JSON 콘텐츠가 포함된 깨끗한 오류가 표시된다.

```json
{ "message": "Oops! yolo did somthing, There goes a rainbow..."}
```



## 기본 예외 처리기를 재정의

FastAPI에는 몇 가지 기본 예외 처리기가 있다. 이러한 핸들러는 `HTTPException` `rasie` 요청에 잘못된 데이터가 있는 경우 기본 JSON 응답을 반환하는 역할을 한다.

이러한 예외 처리기를 사용자 고유의 예외 처리기로 재정의할 수 있다.


### 요청 검증 예외 재정의

요청에 잘못된 데이터가 포함되어 있으면 FastAPI는 내부적으로 `RequestValidationError`를 발생시킨다. 여기에는 기본 예외 처리기도 포함되어 있다.

이를 재정의하려면 `RequestValidationError`를 가져와서 `@app.exception_handler(RequestValidationError)`와 함께 사용하여 예외 처리기를 재정의한다.

예외 처리기는 `Request`와 예외를 받는다.

```python
from fastapi import FastAPI, HTTPException
from fastapi.exceptions import RequestValidationError
from fastapi.responses import PlainTextResponse
from starlette.exceptions import HTTPException as StarletteHTTPException

app = FastAPI()


@app.exception_handler(StarletteHTTPException)
async def http_exception_handler(request, exc):
    return PlainTextResponse(str(exc.detail), status_code=exc.status_code)


@app.exception_handler(RequestValidationError)
async def validation_exception_handler(request, exc):
    return PlainTextResponse(str(exc), status_code=400)


@app.get("/items/{item_id}")
async def read_item(item_id: int):
    if item_id == 3:
        raise HTTPException(status_code=418, detail="Nope! I don't like 3.")
    return {"item_id": item_id}
```

이제 `/items/foo`로 이동하면 다음과 같은 기본 JOSN 오류가 발생하는 대신

```json
{
    "detail": [
        {
            "loc": [
                "path",
                "item_id"
            ],
            "msg": "value is not a valid integer",
            "type": "type_error.integer"
        }
    ]
}
```

다음 내용이 포함된 텍스트 버전을 받게 된다.

```text
1 validation error
path -> item_id
  value is not a valid integer (type=type_error.integer)
```



## `HTTPException` 오류 핸들러 재정의


같은 방식으로 `HTTPException` 핸들러를 재정의할 수 있다. 예를 들어, 다음 오류에 대해 JSON 대신 일반 텍스트 응답을 반환할 수 있다.

```python
from fastapi import FastAPI, HTTPException
from fastapi.exceptions import RequestValidationError
from fastapi.responses import PlainTextResponse
from starlette.exceptions import HTTPException as StarletteHTTPException

app = FastAPI()


@app.exception_handler(StarletteHTTPException)
async def http_exception_handler(request, exc):
    return PlainTextResponse(str(exc.detail), status_code=exc.status_code)


@app.exception_handler(RequestValidationError)
async def validation_exception_handler(request, exc):
    return PlainTextResponse(str(exc), status_code=400)


@app.get("/items/{item_id}")
async def read_item(item_id: int):
    if item_id == 3:
        raise HTTPException(status_code=418, detail="Nope! I don't like 3.")
    return {"item_id": item_id}
```


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/handling-errors/](https://fastapi.tiangolo.com/ko/tutorial/handling-errors/)