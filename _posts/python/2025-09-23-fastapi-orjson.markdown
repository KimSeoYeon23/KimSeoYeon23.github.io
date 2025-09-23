---
layout: post
title: "ORJSONResponse"
date: 2025-09-23 10:14:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## ORJSONResponse

기본적으로 FastAPI 응답을 `JSONResponse`를 사용하여 반환한다. 이를 재정의하려면 `Response`를 직접 반환하면 된다. 그러나 `Response`(또는 `JSONResponse`와 같은 하위 클래스)를 직접 반환하면, 데이터가 자동으로 변환되지 않으며 (심지어 `response_model`을 선언했더라도), 문서화가 자동으로 생성되지 않는다.(예를 들어, 생성된 OpenAPI에 일부러 HTTP 헤더 `Content-type`에 특정 "미디어 타입"을 포함하는 경우)

하지만 경로 작업 데코레이터에서 `response_class` 매개변수를 사용하여 원하는 `Response`(예: 모든 `Response` 하위 클래스)를 선언할 수도 있다. 경로 작업 함수에서 반환하는 내용은 해당 `Response`안에 포함된다.

그리고 만약 그 `Response`가 `JSONResponse`와 `UJSONResponse`의 경우처럼 JSON 미디어 타입(`application/json`)을 가지고 있다면, 경로 작업 데코레이터에서 선언한 Pydantic의 `response_model`을 사용해 자동으로 변환(및 필터링) 된다.

> 미디어 타입이 없는 응답 클래스를 사용하는 경우, FastAPI는 응답에 내용이 없을 것으로 예상하므로 생성된 OpenAPI 문서에서 응답 형식을 문서화하지 않는다.


## ORJSONResponse 사용하기

예를 들어, 성능을 극대화하려는 경우, `orjson`을 설치하여 사용하고 응답을 `ORJSONResponse`로 설정할 수 있다.

사용하고자 하는 `Response` 클래스(하위 클래스)를 임포트한 후, 경로작업 데코레이터에서 선언한다. 

대규모 응답의 경우, 딕셔너리를 반환하는 것보다 `Response`를 반환하는 것이 훨씬 빠르다. 이유는 기본적으로, FastAPI가 내부의 모든 항목을 검사하고 JOSN으로 직렬화할 수 있는지 확인하기 때문이다. 이를 통해 데이터베이스 모델과 같은 임의의 객체를 반환할 수 있다.

하지만 반환하는 내용이 JSON으로 직렬화 가능하다고 확신하는 경우, 해당 내용을 응답 클래스에 직접 전달할 수 있으며, FastAPI가 반환 내용을 `jsonable_encoder`를 통해 처리한 뒤 응답 클래스에 전달하는 오버헤드를 피할 수 있다.

```python
from fastapi import FastAPI
from fastapi.response import ORJSONResponse

app = FastAPI()

@app.get("/items/", response_class=ORJSONResponse)
async def read_items():
	return ORJSONResponse([{"item_id": "Foo"}])
```

> `response_class` 매개변수는 응답의 "미디어 타입"을 정의하는 데에도 사용된다.
> 이 경우, HTTP 헤더 `Content-Type`은 `application/json`으로 설정된다.
> 그리고 이는 OpenAPI에 그대로 문서화된다.

> [Tip] `ORJSONResponse`는 FastAPI에서만 사용할 수 있다.



> 출처: [https://fastapi.tiangolo.com/ko/advanced/custom-response/](https://fastapi.tiangolo.com/ko/advanced/custom-response/)