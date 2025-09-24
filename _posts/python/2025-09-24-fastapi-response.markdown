---
layout: post
title: "Response"
date: 2025-09-24 09:14:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 응답을 직접 반환하기

FastAPI에서 경로 작업(path operation)을 생성할 때, 일반적으로 `dict`, `list`, Pyadantic 모델, 데이터베이스 모델 등의 데이터를 반환할 수 있다.

기본적으로 FastAPi는 [JSON 호환 가능 인코더](https://fastapi.tiangolo.com/ko/tutorial/encoder/)에 설명된 `jsonable_encoder`를 사용해 해당 반환 값을 자동으로 `JSON`으로 변환한다. 그런 다음, JSON 호환 데이터(예: `dict`)를 `JSONResponse`에 넣어 사용자의 응답을 전송하는 방식으로 처리된다.

그러나 경로 작업에서 `JSONResponse`를 직접 반환할 수도 있다. 예를 들어, 사용자 정의 헤더나 쿠키를 반환해야 하는 경우에 유용할 수 있다.

## `Response` 반환하기

사실, `Response` 또는 그 하위 클래스를 반환할 수 있다.

> `JSONResponse` 자체도 `Response`의 하위 클래스이다.

그리고 `Response`를 반환하면 FastAPI가 이를 그대로 전달한다. Pydantic 모델로 데이터 변환을 수행하지 않으며, 내용을 다른 형식으로 변환하지 않는다. 이로 인해 많은 유연성을 얻을 수 있다. 어떤 데이터 유형이든 반환할 수 있고, 데이터 선언이나 유효성 검사를 재정의할 수 있다.


## `Response`에서 `jsonable_encoder` 사용하기

FastAPI는 반환하는 `Response`에 아무런 변환을 하지 않으므로, 그 내용이 준비되어 있어야 한다.
예를 들어, Pydantic 모델을 `dict`로 변환해 `JSONResponse`에 넣지 않으면 JSON 호환 유형으로 변환된 데이터 유형(예: `datetime`, `UUID` 등)이 사용되지 않는다.

이러한 경우, 데이터를 응답에 전달하기 전에 `jsonable_encoder`를 사용하여 변환할 수 있다.

```python
from datetiem import datetime
from typing import Union

from fastapi import FastAPI
from fastapi.encoders import jsonable_encoder
from fastapi.response import JSONResponse
from pydantic improt BaseModel

class Item(BaseModel):
	title: str
	timestamp: datetime
	description: Union[str, None] = None
	
app = FastAPI()

@app.put("/items/{id}")
def update_time(id: str, item: Item):
	json_compatible_item_data = jsonable_encoder(item)
	return JSONResponse(content=json_compatible_item_data)
```


## 사용자 정의 `Response` 반환하기

데이터를 직접 반환하면 FastAPI가 이를 `JSONResponse`에 넣고 `dict`로 변환하는 등 모든 작업을 자동으로 처리한다.

이제, 사용자 정의 응답을 반환하는 방법을 알아본다. 예를 들어 XML 응답을 반환하고 싶다고 가정해보겠다. XML 내용을 문자열에 넣고, 이를 `Response`에 넣어 반환할 수 있다.

```python
from fastapi import FastAPI, Response

app = FastAPI()

@app.get("/legacy/")
def get_legacy_data():
    data = """<?xml version="1.0"?>
    <shampoo>
    <Header>
        Apply shampoo here.
    </Header>
    <Body>
        You'll have to use soap here.
    </Body>
    </shampoo>
    """
    return Response(content=data, media_type="application/xml")
```



> 출처: [https://fastapi.tiangolo.com/ko/advanced/response-directly/](https://fastapi.tiangolo.com/ko/advanced/response-directly/)