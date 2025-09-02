---
layout: post
title: "FastAPI 폼 데이터"
date: 2025-09-02 09:52:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 폼 데이터

## 폼 데이터

JSON 대신 폼 필드를 받아야 하는 경우 `Form`을 사용할 수 있다.

> 폼을 사용하려면, 먼저 `python-multipart`를 설치한다.
> 가상 환경을 생성하고 활성화한 다음, 아래와 같이 설치할 수 있다.
> `pip install python-multipart`


## `Form` 임포트하기

`fastapi`에서 `Form`을 임포트한다.

```python
from typing import Annotated
from fastapi import FastAPI, Form

app = FastAPI()

@app.post("/login")
async def login(username: Annotated[str, Form()], password: Annotated[str, Form()]):
	return {"username": username}
```


## `Form` 매개변수 정의하기

`Body` 또는 `Query`와 동일한 방식으로 폼 매개변수를 만든다.

```python
from typing import Annotated
from fastapi import FastAPI()

app = FastAPI()

@app.post("/login")
async def login(username: Annotated[str, Form()], password: Annotated[str, Form()]):
	return {"username": username}
```

예를 들어 OAuth2 사양을 사용할 수 있는 방법 중 하나("패스워드 플로우"라고 함)로 `username`과 `password`를 폼 필드로 보내야 한다.

사양에서는 필드 이름이 `username` 및 `password`로 정확하게 명명되어야 하고, JSON이 아닌 폼 필드로 전송해야 한다.

`Form`을 사용하면 유효성 검사, 예제, 별칭(예: `username` 대신 `user-name`) 등을 포함하여 `Body`(및 `Query`, `Path`, `Cookie`)와 동일한 구성을 선언할 수 있다.



> `Form`은 `Body`에서 직접 상속되는 클래스이다.
> 폼 본문을 선언할 때, 폼이 없으면 매개변수가 쿼리 매개변수나 본문(JSON) 매개변수로 해석(interpret)되기 때문에 `Form`을 명시적으로 사용해야 한다.


## 폼 필드에 대해

HTML 폼(`<form></form>`)이 데이터를 서버로 보내는 방식은 일반적으로 해당 데이터에 대해 "특수" 인코딩을 사용하며, 이는 JSON과 다르다.

**FastAPI**는 JSON 대신 올바른 위치에서 해당 데이터를 읽는다.

폼의 데이터는 일반적으로 "미디어 유형(media type)" `application/x-www-form-urlencoded`를 사용하여 인코딩한다. 그러나 폼에 파일이 포함된 경우, `multipart-form-data`로 인코딩한다. 



> 출처: [https://fastapi.tiangolo.com/ko/tutorial/request-forms/](https://fastapi.tiangolo.com/ko/tutorial/request-forms/)