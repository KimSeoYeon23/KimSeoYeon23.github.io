---
layout: post
title: "FastAPI 응답 상태 코드"
date: 2025-09-01 09:42:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 응답 상태 코드

## 응답 상태 코드

응답 모델과 같은 방법으로, 어떤 라우트이든 `status_code` 매개변수를 사용하여 응답에 대한 HTTP 상태 코드를 선언할 수 있다.

- `@app.get()`
- `@app.post()`
- `@app.put()`
- `@app.delete()`
- 기타

```python
from fastapi import FastAPI

app = FastAPI()

@app.post("/items", status_code=201)
async def create_item(name: str):
	return {"name": name}
```


> `status_code`는 "데코레이터" 메소드(`get`, `post` 등의)의 매개변수이다. 모든 매개변수들과 본문처럼 라우트 함수가 아니다.


`status_code`매개 변수는 HTTP 상태 코드를 숫자로 입력받는다.

> `status_code`는 파이썬의 `http.HTTPStatus`와 같은 `IntEnum`을 입력받을 수도 있다.


`status_code` 매개변수는

- 응답에서 해당 상태 코드를 반환한다.
- 상태 코드를 OpenAPI 스키마(및 사용자 인터페이스)에 문서화한다.


![](https://i.imgur.com/WVJWkWQ.png)



## HTTP 상태 코드에 대하여

HTTP는 세자리의 숫자 상태 코드를 응답의 일부로 전송한다.

이 상태 코드들은 각자를 식별할 수 있도록 지정된 이름이 있으나, 중요한 것은 숫자 코드이다.

- `1xx` 상태 코드는 "정보"용이다. 이들은 직접적으로는 잘 사용되지는 않는다. 이 상태 코드를 갖는 응답들은 본문을 가질 수 없다.
- `2xx` 상태 코드는 "성공적인" 응답을 위해 사용된다. 가장 많이 사용되는 유형이다
	- `200`은 디폴트 상태 코드로, 모든 것이 "성공적임"을 의미한다.
	- 다른 예로는 `201` "생성됨" 이 있다. 일반적으로 데이터베이스에 새로운 레코드를 생성한 후 사용한다.
	- 단, `204` "내용 없음"은 특별한 경우이다. 이것은 클라이언트에게 반환할 내용이 없는 경우 사용한다. 따라서 응답은 본문을 가질 수 없다.
- `3xx` 상태 코드는 "리다이렉션"  이다. 본문을 가질 수 없는 `304` "수정되지 않음"을 제외하고, 이상태 코드를 갖는 응답에는 본문이 있을 수도, 없을 수도 있다.
- `4xx` 상태 코드는 "클라이언트 오류" 응답을 위해 사용된다. 이것은 아마 가장 많이 사용하게 도리 두번째 유형이다.
	- 일례로 `404`는 "찾을 수 없음" 응답을 위해 사용한다.
	- 일반적으로 클라이언트 오류의 경우 `400`을 사용할 수 있다.
- `5xx` 상태 코드는 서버 오류에 상요된다. 이것들을 직접 사용할 일은 거의 없다. 응용 프로그램 코드나 서버의 일부에 문제가 발생하면 자동으로 이들 상태 코드 중 하나를 반환한다.


```python
from fastapi import FastAPI

app = FastAPI()


@app.post("/items/", status_code=201)
async def create_item(name: str):
    return {"name": name}
```

`201`은 "생성됨"을 의미하는 상태 코드이다. 하지만 모든 상태 코드들이 무엇을 의미하는지 외울 필요는 없다. `fastapi.status`의 편의 변수를 사용할 수 있다.

```python
from fastapi import FastAPI, status

app = FastAPI()

@app.post("/items", status_code=status.HTTP_201_CREATED)
async def create_item(name: str):
	return {"name": name}
```

이것은 단순히 작업을 편리하게 하기 위한 것으로, HTTP 상태 코드와 동일한 번호를 갖고 있다.


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/response-status-code/](https://fastapi.tiangolo.com/ko/tutorial/response-status-code/)