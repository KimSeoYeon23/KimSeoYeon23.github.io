---
layout: post
title: "OAuth2PasswordBearer"
date: 2025-09-26 09:41:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 `OAuth2PasswordBearer`

FastAPI는 이러한 보안 기능을 구현하기 위해 다양한 추상화 수준에서 여러 도구를 제공한다.
이 예제에서는 OAuth2와 Password 흐름을 사용해 Bearer token을 활용할 것이다. 그러기 위해 `OAuth2PasswordBearer` 클래스를 사용한다.

`OAuth2PasswordBearer` 클래스의 인스턴스를 생성할 때 `tokenUrl`에 매개변수를 전달한다. 매개변수는 클라이언트(유저의 브라우저에서 실행 중인 프론트엔드)가 토큰을 획득하기 위해 `username`과 `password`를 전송할 때 사용할 URL을 포함한다.

```python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/items/")
async def read_items(token: Annotated[str, Depends(oauth2_scheme)]):
	return {"token": token}
```

> 여기서 `tokenUrl="token"`은 아직 생성하지 않은 상대 URL `token`을 나타낸다. 상태 URL이므로 `./token`과 동일하다.
> 상대 URL을 사용하고 있으므로 API가 `https://example.com/`에 있는 경우 `https://example.com/token`을 참조하게 된다. 하지만 API가 `https://example.com/api/v1/`에 있는 경우 `https://example.com/api/v1/token`을 참조하게 된다.

이 매개 변수는 엔드포인트 `/` 경로 작업을 생성하지 않지만, 클라이언트가 토큰을 가져오는 데 사용할 URL이 `/token` 임을 선언한다. 이 정보는 OpenAPI에서 사용되며, 이후 대화형 API 문서 시스템에서도 사용된다.

`oauth2_scheme` 변수는 `OAuth2PasswordBearer`의 인스턴스이지만 "호출 가능" 변수이기도 하다.

다음과 같이 호출할 수도 있다.

```python
oauth2_scheme(some, parameters)
```

따라서 `Depends`와 함께 사용할 수 있다.


## Use it

이제 `Depends`를 사용하여 `oauth2_sceheme`를 종속성에 전달할 수 있다.

```python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/items/")
async def read_items(token: Annotated[str, Depends(oauth2_scheme)]):
	return {"token": token}
```

이 종속성은 경로 작업 함수의 매개변수 `token`에 할당된 `str`을 제공한다.
FastAPI는 이 종속성을 사용하여 OpenAPI 스키마(및 자동 API 문서)에서 보인 "보안 체계"를 정의할 수 있다는 것을 알게 된다.

> FastAPI는 `fastapi.security.oauth2.OAuth2`에서 상속받고, `fastapi.security.oauth2.OAuth2`는 다시 `fastapi.security.base.SecurityBase`에서 상속받기 때문에 OpenAPI에서 보안 체계를 정의하기 위해 종속성에서 선언된 클래스 `OAuth2PasswordBearer`를 사용할 수 있다는 것을 알게 된다.


## What it does

이 함수는 요청에서 해당 `Authorization` 헤더를 살펴보고, 값이 `Bearer`와 토큰으로 구성되어 있는지 검사한 후 토큰을 `str`로 반환한다. `Authorization` 헤더가 없거나 `Bearer` 토큰이 없느 ㄴ경우 401 상태 코드 오류(`UNAUTHORIZED`)를 직접 반환한다.

오류를 바환하기 위해 토큰이 존재하는지 확인할 필요조차 없다. 함수가 실행되면 해당 토큰에 `str`이 포함되어 있음을 확신할 수 있다.


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/security/first-steps/#fastapis-oauth2passwordbearer](https://fastapi.tiangolo.com/ko/tutorial/security/first-steps/#fastapis-oauth2passwordbearer)