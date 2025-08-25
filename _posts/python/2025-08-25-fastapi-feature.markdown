---
layout: post
title: "FastAPI 기능"
date: 2025-08-25 10:42:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 기능

### 개방형 표준을 기반으로

- 경로(엔드포인트, 라우트) 작동(POST, PUT, GET, DELETE와 같은 HTTP 메소드), 매개변수, 본문 요청, 보안 그 외의 선언을 포함한 API 생성을 위한  [**OpenAPI**](https://github.com/OAI/OpenAPI-Specification)
- - [**JSON Schema**](https://json-schema.org/) (OpenAPI 자체가 JSON Schema를 기반으로 하고 있다)를 사용한 자동 데이터 모델 문서화.
- 다양한 언어로 자동적인 클라이언트 코드 생성을 사용할 수 있게 지원한다.


### 문서 자동화

대화형 API 문서와 웹 탐색 유저 인터페이스를 제공한다. 프레임워크가 OpenAPI를 기반으로 하기에, 2가지 옵션이 기본적으로 들어간 여러 옵션이 존재한다.

- 대화형 탐색 [**Swagger UI**](https://github.com/swagger-api/swagger-ui)를 이용해, 브라우저에서 바로  API를 호출하거나 테스트할 수 있다.

![](https://i.imgur.com/582L6xU.png)

- [**ReDoc**](https://github.com/Rebilly/ReDoc)을 이용해 API 문서화를 대체할 수 있다.

![](https://i.imgur.com/3WuOhEo.png)


### 그저 현대 파이썬

(Pydantic 덕분에) FastAPI는 표준 파이썬 3.6 타입 선언에 기반하고 있다. 새로 배울 문법이 없다.

타입을 잉요한 표준 파이썬을 다음과 같이 적을 수 있다.

```python
from datetime import date
from pydantic import BaseModel

# 변수를 str로 선언
# 그 후 함수 안에서 편집기 지원을 받는다.
def main(user_id: str):
	return user_id

# pydantic 모델
class User(BaseModel):
	id: int
	name: str
	joined: date
```

위의 코드는 다음과 같이 사용될 수 있다.

```python
my_user: User = User(id=3, name="John Doe", joined="2018-07-19")

second_user_data={
	"id": 4,
	"name": "Mary",
	"joined": "2018-11-30",
}

my_second_user: User = User(**second_user_data)
```

> `**second_user_data`가 뜻하는 것:
> `second_user_data` 딕셔너리의 키와 값을 키-값 인자로서 바로 넘겨준다. 다음과 동일하다:
> `User(id=4, name="Mary", joined="2018-11-30"`


### 검증

- 다음을 포함한, 대부분의 파이썬 데이터 타입 검증을 할 수 있다.
	- JSON 객체(`dict`)
	- 아이템 타입을 정의하는 JSON 배열(`list`)
	- 최소 길이와 최대 길이를 정의하는 문자열(`str`) 필드
	- 최솟값과 최댓값을 가지는 숫자(`int`, `float`), 그 외
- 다음과 같이 더욱 이색적인 타입에 대해 검증할 수 있다.
	- URL
	- 이메일
	- UUID
	- ... 다른 것들

모든 검증은 견고하면서 잘 확립된 **Pydantic**에 의해 처리된다.


### 보안과 인증

보안과 인증이 통합되어 있다. 데이터베이스나 데이터 모델과의 타협없이 사용할 수 있다.
다음을 포함하는, 모든 보안 스키마가 OpenAPI에 정의되어 있다.

- HTTP Basic
- OAuth2  (JWT Tokens 또한 포함) [OAuth2 with JWT](https://fastapi.tiangolo.com/ko/tutorial/security/oauth2-jwt/)
- 다음에 들어 있는 API 키
	- 헤더
	- 매개변수
	- 쿠키 및 그 외

추가적으로 (세션 쿠키를 포함한) 모든 보안 기능은 Starlette에 있다.

모두 재사용할 수 있는 도구와 컴포넌트로 만들어져 있어 시스템, 데이터 저장소, 관계형 및 NoSQL 데이터베이스 등과 쉽게 통합할 수 있다.


### 의존성 주입

FastAPI는 사용하기 매우 간편하지만 엄청난 **의존성 주입**(컴포넌트, 자원, 서비스, 제공자로도 알려진) 시스템을 포함하고 있다.

- 의존성은 의존성을 가질 수도 있어, 이를 통해 의존성의 계층이나 **의존성의 "그래프"** 를 형성한다.
- 모든 것이 프레임워크에 의해 **자동적으로 처리된다.**
- 모든 의존성은 요청에서 데이터를 요구하여 자동 문서화와 **경로 작동 제약을 강화할 수 있다.**
- 의존성에서 정의된 *경로 작동* 매개변수에 대해서도 **자동 검증**이 이루어 진다.
- 복잡한 사용자의 인증 시스템, **데이터 베이스 연결**, 등등을 지원한다.


##  Starlette 기능

**FastAPI**는 [**Starlette**](https://www.starlette.io/)를 기반으로 구축되었으며, 이와 완전히 호환된다. 

`FastAPI`는 실제로 `Starlette`의 하위 클래스이다. 그래서, 이미 Starlette을 이미 알고 있거나 사용하고 있으면, 대부분의 기능이 같은 방식으로 작동할 것이다.

**FastAPI**를 사용하면 **Starlette**의 기능 대부분을 얻게 될 것이다.(FastAPI가 단순히 Starlette를 강화했기 때문이다.)

- NodeJS와 Go와 동등하게 사용 가능한 가장 빠른 파이썬 프레임워크 중 하나이다.
- WebSocket 지원
- 프로세스 내의 백그라운드 작업
- 시작과 종료 이벤트
- HTTPX 기반 테스트 클라이언트
- CORS, GZip, 정적 파일, 스트리밍 응답
- 세션과 쿠키 지원
- 100% 테스트 범위
- 100% 타입이 명시된 코드 베이스


## Pydantic 기능

**FastAPI**는 [**Pydantic**](https://docs.pydantic.dev/)을 기반으로 하며 Pydantic과 완벽하게 호환된다.
Pydantic을 기반으로 하는 데이터베이스를 위한 ORM, ODM을 포함한 외부 라이브러리를 포함한다.
이는 모든 것이 자동으로 검증되기 때문에, 많은 경우에서 요청을 통해 얻은 동일한 객체를, **직접 데이터베이스로** 넘겨줄 수 있다.

반대로도 마찬가지이며, 많은 경우에서 **직접 클라이언트로** 객체를 넘겨줄 수 있다.

- **어렵지 않은 언어**
	- 새로운 스키마 정의 마이크로 언어를 배우지 않아도 된다.
- Pydantic 데이터 구조는 단순 정의한 클래스의 인스턴스이기 때문에, 자동 완성, 린팅, mypy 그리고 우리의 직관까지 우리의 검증된 데이터와 올바르게 작동한다.
- **복잡한 구조**를 검증한다.
	- 계층적인 Pydantic 모델, 파이썬 `typing`의 `List`와 `Dict`, 그 외를 사용한다.
	- 그리고 검증자는 복잡한 데이터 스키마를 명확하고 쉽게 정의 및 확인하며 JSON 스키마로 문서화한다.
	- 깊게 **중첩된 JSON** 객체를 가질 수 있으며, 이 객체 모두 검증하고 설명을 붙일 수 있다.
- **확장 가능성**
	- Pydantic은 사용자 정의 데이터 타입을 정의할 수 있게 하거나, 검증자 데코레이터가 붙은 모델의 메소드를 사용하여 검증을 확장할 수 있다.


> 출처: [https://fastapi.tiangolo.com/ko/features/](https://fastapi.tiangolo.com/ko/features/)