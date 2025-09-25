---
layout: post
title: "Dataclasses"
date: 2025-09-25 10:51:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 데이터 클래스 사용

FastAPI는 Pydantic을 기반으로 구축되었으며, Pydantic 모델을 사용하여 요청과 응답을 선언하는 방법들이있다. 하지만 FastAPI는 동일한 방식으로 `dataclasses`를 사용하는 것도 지원한다.

```python
from dataclasses import dataclass
from typing import Union

from fastapi import FastAPI

@dataclass
class Item:
	name: str
	price: float
	description: Union[str, None] = None
	tax: Union[float, None] = None

app = FastAPI()

@app.post("/items/")
async def create_item(item: Item):
	return item
```

Pydantic은 내부적으로 `dataclasses`를 지원한다. 따라서 Pydanticㅇ르 명시적으로 사용하지 않는 위의 코드에서도 FastAPI는 Pydanticㅇ르 사용하여 표준 데이터 클레스를 Pydantic의 고유한 데이터 클래스로 변환한다.

물론, Pydantic과 `dataclasses`와 동일한 것을 지원한다.

- 데이터 검증
- 데이터 직렬화
- 데이터 문서화 등

이는 Pydantic 모델과 동일한 방식으로 작동한다. 실제로 Pydantic을 사용하여 아래에서 동일한 방식으로 구현된다.

> `dataclasses`가 Pydantic 모델이 할 수 있는 모든 일을 할 수 없다는 점을 명심해야 한다.


## `response_mdoel`의 데이터 클래스

`response_model` 매개변수에서 `dataclasses`를 사용할 수도 있다.

```python
from dataclasses import dataclass, field
from typing import List, Union

from fastapi import FastAPI

@dataclass
class Item:
	name: str
	price: float
	description: Union[str, None] = None
	tax: Union[float, None] = None

app = FastAPI()

@app.get("/items/next", response_model=Item)
async def read_next_item():
	return {
		"name": "Island In The Moon",
		"price": 12.99,
		"description": "A place to be playin' and havin' fun",
		"tags": ["breater"]
	}
```

데이터 클래스는 자동으로 Pydantic 데이터 클래스로 변환된다. 이렇게 하면 해당 스키마가 API 문서 사용자 인터페이스에 표시된다.

![](https://i.imgur.com/0Yo2mK4.png)


## 중첩된 데이터 구조에서의 Dataclasses

데이터 클래스를 다른 타입 주석과 결합하여 중첩된 데이터 구조를 만들 수도 있다. 경우에 따라 Pydantic 버전의 `dataclasses`를 사용해야 할 수도 있다. 예를 들어, 자동 생성된 API 문서에 오류가 있는 경우이다. 그런 경우에는 표준 `dataclasses`를 `pydantic.dataclasses`로 교체하면 된다. 

```python
from dataclasses import field  # (1)
from typing import List, Union

from fastapi import FastAPI
from pydantic.dataclasses import dataclass  # (2)


@dataclass
class Item:
    name: str
    description: Union[str, None] = None


@dataclass
class Author:
    name: str
    items: List[Item] = field(default_factory=list)  # (3)


app = FastAPI()


@app.post("/authors/{author_id}/items/", response_model=Author)  # (4)
async def create_author_items(author_id: str, items: List[Item]):  # (5)
    return {"name": author_id, "items": items}  # (6)


@app.get("/authors/", response_model=List[Author])  # (7)
def get_authors():  # (8)
    return [  # (9)
        {
            "name": "Breaters",
            "items": [
                {
                    "name": "Island In The Moon",
                    "description": "A place to be playin' and havin' fun",
                },
                {"name": "Holy Buddies"},
            ],
        },
        {
            "name": "System of an Up",
            "items": [
                {
                    "name": "Salt",
                    "description": "The kombucha mushroom people's favorite",
                },
                {"name": "Pad Thai"},
                {
                    "name": "Lonely Night",
                    "description": "The mostests lonliest nightiest of allest",
                },
            ],
        },
    ]
```


1. 우리는 여전히 표준 `dataclasses` 에서 `field`를 가져온다.
2. `pydantic.dataclasses`는 `dataclasses`를 대체할 수 있다.
3. `Author` 데이터 클래스에는 `Item` 데이터 클래스 목록이 포함되어 있다.
4. `Author` 데이터 클래슨느 `response_model`의 매개변수로 사용된다.
5. 요청 본문으로 데이터 클래스와 함께 다른 표준 유형 주석을 사용할 수 있다. 이 경우에는 `Item` 데이터 클래스의 목록이다.
6. 여기서 `items` 에 포함하는 dict를 반환하는데, 이는 데이터 클래스의 목록이다.
7. 여기서 `response_model`은 `Author` 데이터 클래스 목록 유형의 주석을 사용한다. 다시 말해, `dataclasses`  와 표준 유형 주석을 결합할 수 있다.
8. 이 경로 작업 함수는 `async def` 대신 일반 `def`를 사용한다는 점에 유의한다.
9. 이 경로 작업 함수는 데이터 클래스를 반환하지 않지만(반환할 수도 있지만) 내부 데이터가 있는 dict를 반환한다.


> 출처: [https://fastapi.tiangolo.com/ko/advanced/dataclasses/](https://fastapi.tiangolo.com/ko/advanced/dataclasses/)