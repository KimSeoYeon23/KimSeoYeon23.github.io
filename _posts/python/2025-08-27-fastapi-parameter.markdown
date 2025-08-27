---
layout: post
title: "FastAPI 경로 매개변수"
date: 2025-08-27 09:45:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 경로 매개변수

## 경로 매개변수

파이썬의 포맷 문자열 리터럴에서 사용되는 문법을 이용하여 경로 "매개변수" 또는 "변수"를 선언할 수 있다.

```python
from fastapi import FastAPI  
  
app = FastAPI()  
    
@app.get('/items/{item_id}')  
async def read_item(item_id):  
    return {"item_id": item_id}
```

경로 매개변수 `item_id`의 값은 함수의 `item_id` 인자로 전달된다.
그래서 이 예제를 실행하고 [http://127.0.0.1:8000/items/foo](http://127.0.0.1:8000/items/foo)로 이동하면, 다음 응답을 볼 수 있다.

```json
{"item_id":"foo"}
```


## 타입이 있는 매개변수

파이썬 표준 타입 어노테이션을 사용하여 함수에 있는 경로 매개변수의 타입을 선언할 수 있다.

```python
from fastapi import FastAPI  
  
app = FastAPI()  
  
@app.get('/items/{item_id}')  
async def read_item(item_id: int):  
    return {"item_id": item_id}
```

위의 예시에서 `item_id`는 `int`로 선언되었다.

### 데이터 변환

이 예제를 실행하고 [http://127.0.0.1:8000/items/3](http://127.0.0.1:8000/items/3)을 열면, 다음 응답을 볼 수 있다.

```json
{"item_id":3}
```

> 함수가 받은(반환도 하는) 값은 문자열 `"3"`이 아니라 파이썬 `int` 형인 `3`이다.
> 즉, 타입 선언을 하면 **FastAPI**는 자동으로 요청을 "파싱" 한다.


### 데이터 검증

하지만 브라우저에서 [http://127.0.0.1:8000/items/foo](http://127.0.0.1:8000/items/foo)로 이동하면, HTTP 오류가 잘 뜨는 것을 확인할 수 있다.

```json
{
  "detail": [
    {
      "type": "int_parsing",
      "loc": [
        "path",
        "item_id"
      ],
      "msg": "Input should be a valid integer, unable to parse string as an integer",
      "input": "foo"
    }
  ]
}
```

경로 매개변수 `item_id`는 `int`가 아닌 `"foo"` 값이기 때문이다.

`int`가 아닌 `float`을 전달하는 경우에도 동일한 오류가 나타난다 [http://127.0.0.1:8000/items/4.2](http://127.0.0.1:8000/items/4.2)

> 즉, 파이썬 타입 선언을 하면 **FastAPI**는 데이터 검증을 한다.
> 오류에는 정확히 어느 지점에서 검증을 통과하지 못했는지 명시된다.
> 이는 API와 상호 ㅈ가용하는 코드를 개발하고 디버깅하는 데 매우 유용하다.


## 문서화

브라우저에서 [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)를 열면, 다음과 같이 자동 대화식 API 문서를 볼 수 있다.

![](https://i.imgur.com/6fmwySA.png)


### 표준 기반의 이점, 대체 문서

그리고 생성된 스키마는 OpenAPI 표준에서 나온 것이기 때문에 호환되는 도구가 많이 있다.
이 덕분에 **FastAPI**는 [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)로 접속할 수 있는 (ReDoc을 사용하는) 대체 API 문서를 제공한다.

![](https://i.imgur.com/hHyTKaX.png)

이와 마찬가지로 다양한 언어에 대한 코드 생성 도구를 포함하여 여러 호환되는 도구가 있다.


## Pydantic

모든 데이터 검증은 Pydantic에 의해 내부적으로 수행되므로 이로 인한 이점을 모두 얻을 수 있다. 

`str`, `float`, `bool`, 그리고 다른 여러 복잡한 데이터 타입 선언을 할 수 있다.



## 순서 문제

라우트(경로 작동)을 만들 때 고정 경로를 갖고 있는 상황들을 맞닥뜨릴 수 있다.

`/users/me` 처럼, 현재 사용자의 데이터를 가져온다고 할 때, 사용자 ID를 이용해 특정 사용자의 정보를 가져오는 경로 `/users/{user_id}`도 있다.

라우트는 순차적으로 실행되기 때문에 `/users/{user_id}` 이전에 `/users/me`를 먼저 선언해야 한다.

```python
from fastapi import FastAPI  
  
app = FastAPI()  
  
@app.get("/users/me")  
async def read_user_me():  
    return {"user_id": "the current user"}  
  
@app.get("/users/{user_id}")  
async def read_user(user_id: str):  
    return {"user_id": user_id}
```

그렇지 않으면 `/users/{user_id}`는 `/users/me` 요청 또한 매개변수 `user_id`의 값이 `"me"`인 것으로 "생각하게" 된다.


## 사전 정의 값

만약 경로 매개변수를 받는 라우트가 있지만, 경로 매개변수로 가능한 값들을 미리 정의하고 싶다면 파이썬 표준 `Enum`을 사용할 수 있다.


### `Enum` 클래스 생성

`Enum`을 임포트하고 `str`과 `Enum`을 상속하는 서브 클래스를 만든다.

`str`을 상속함으로써 API 문서는 값이 `string` 형이어야 하는 것을 알게 되고 이는 문서에 제대로 표시된다.

가능한 값들에 해당하는 고정된 값의 클래스 attributes들을 만든다.

```python
from enum import Enum  
from fastapi import FastAPI  
  
class ModelName(str, Enum):  
    alexnet = "alexnet"  
    resnet = "resnet"  
    lenet = "lenet"  
```


### 경로 매개변수 선언

생성한 열거형(`Enum`) 클래스(`ModelName`)를 사용하는 타입 어노테이션으로 경로 매개변수를 만든다.

```python
from enum import Enum  
from fastapi import FastAPI  
  
class ModelName(str, Enum):  
    alexnet = "alexnet"  
    resnet = "resnet"  
    lenet = "lenet"  
  
app = FastAPI()  
   
@app.get("/models/{model_name}")  
async def get_model(model_name: ModelName):  
```


### 문서 확인

경로 매개변수에 사용할 수 있는 값은 미리 정의되어 있으므로 Swagger에서 잘 표시된다.

![](https://i.imgur.com/gyE5loc.png)


## 파이썬 열거형(enum)으로 작업하기

경로 매개변수의 값은 열거형 멤버가 된다.


### 열거형 멤버 비교

열거형 `ModelName`의 열거형 멤버를 비교할 수 있다.

```python
from enum import Enum  
from fastapi import FastAPI  
  
class ModelName(str, Enum):  
    alexnet = "alexnet"  
    resnet = "resnet"  
    lenet = "lenet"  
  
app = FastAPI()  
   
@app.get("/models/{model_name}")  
async def get_model(model_name: ModelName):  
    if model_name is ModelName.alexnet:  
        return {"model_name": model_name, "message": "Deep Learning FTW!"}  
  
    if model_name.value == "lenet":  
        return {"model_name": model_name, "message": "LeCNN all the images"}  
  
    return {"model_name": model_name, "message": "Have some residuals"}
```


### 열거형 값 가져오기

`model_name.value` 또는 일반적으로 `your_enum_member.value`를 이용하여 실제 값(위 예시의 경우 `str`)을 가져올 수 있다.

```python
from enum import Enum  
from fastapi import FastAPI  
  
class ModelName(str, Enum):  
    alexnet = "alexnet"  
    resnet = "resnet"  
    lenet = "lenet"  
  
app = FastAPI()  
   
@app.get("/models/{model_name}")  
async def get_model(model_name: ModelName):  
    if model_name is ModelName.alexnet:  
        return {"model_name": model_name, "message": "Deep Learning FTW!"}  
  
    if model_name.value == "lenet":  
        return {"model_name": model_name, "message": "LeCNN all the images"}  
  
    return {"model_name": model_name, "message": "Have some residuals"}
```


### 열거형 멤버 반환

라우트에서 열거형 멤버를 반환할 수 있다. 이는 중첩 JSON 본문(예: `dict`)내의 값으로도 가능하다.

클라이언트에 반환하기 전에 해당 값(이 경우 문자열)으로 변환된다.

```python
from enum import Enum  
from fastapi import FastAPI  
  
class ModelName(str, Enum):  
    alexnet = "alexnet"  
    resnet = "resnet"  
    lenet = "lenet"  
  
app = FastAPI()  
   
@app.get("/models/{model_name}")  
async def get_model(model_name: ModelName):  
    if model_name is ModelName.alexnet:  
        return {"model_name": model_name, "message": "Deep Learning FTW!"}  
  
    if model_name.value == "lenet":  
        return {"model_name": model_name, "message": "LeCNN all the images"}  
  
    return {"model_name": model_name, "message": "Have some residuals"}
```

클라이언트는 아래의 JSON 응답을 얻는다.

```json
{
  "model_name": "alexnet",
  "message": "Deep Learning FTW!"
}
```



## 경로를 포함하는 경로 매개변수

경로를 포함하는 라우트 `/files/{file_path}`이 있다고 해본다.
그런데 이 경우 `file_path` 자체가 `home/johndoe/myfile.txt`와 같은 경로를 포함해야 한다.

이 때 해당 파일의 URL은 다음처럼 된다.
`/files/home/johndoe/myfile.txt`


### OpenAPI 지원

테스트와 정의가 어려운 시나리오로 이어질 수 있으므로 OpenAPI는 경로를 포함하는 경로 매개변수를 내부에 선언하는 방법을 지원하지 않는다.

그럼에도 Starlette의 내부 도구 중 하나를 사용하여 **FastAPI**에서는 이가 가능하다.

문서에 매개변수에 경로가 포함되어야 한다는 정보가 명시되지는 않지만 여전히 작동한다.


### 경로 변환기

Starlette의 옵션을 직접 이용하여 다음과 같은 URL을 사용함으로써 path를 포함하는 경로 매개변수를 선언할 수 있다.

```text
/files/{file_path:path}
```

이러한 경우 매개변수의 이름은 `file_path`이며, 마지막 부분 `:path`는 매개변수가 경로와 일치해야 함을 명시해야 한다.

따라서 다음과 같이 사용할 수 있다.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/files/{file_path:path}")
async def read_file(file_path: str):
	return {"file_path": file_path}
```


> 매개변수가 가져야 하는 값이 `/home/johndoe/myfile.txt`와 같이 슬래시로 시작(`/`)해야 할 수 있다.
> 이 경우 URL은 `/files//home/johndoe/myfile.txt`이며 `files`과 `home` 사이에 이중 슬래시(`//`)가 생긴다.


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/path-params/](https://fastapi.tiangolo.com/ko/tutorial/path-params/)