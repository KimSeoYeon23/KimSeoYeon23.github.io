---
layout: post
title: "SQLAlchemy ORM"
date: 2025-09-12 10:38:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## ORM 라이브러리 설치하기

다음 명령을 수행하여 SQLAlchemy 라이브러리를 설치한다.

```bash
pip install sqlalchemy
#or
uv add sqlalchemy
```


### 설정 파일 추가하기

FastAPI에 ORM을 적용하려면 데이터베이스 설정이 필요하다. 루트 디렉토리에 `database.py` 파일을 생성하고 다음과 같은 코드를 작성한다.

```python
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

SQLALCHEMY_DATABASE_URL = "sqlite:///./myapi.db"

engine = create_engin(
	SQLALCHEMY_DATABASE_URL, connect_args={"check_same_thread": False}
)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)

Base = declarative_base()
```

`SQLALCHEMY_DATABASE_URL`는 데이터베이스 접속 주소이다.

> `sqlite:///./myapi.db"`는 sqlite3 데이터베이스의 파일을 의미하며 프로젝트 루트디렉토리에 저장한다는 의미이다.

그리고 `SessionLocal`은 데이터베이스에 접속하기 위해 필요한 클래스이다. `create_engine`, `sessionamker` 등을 사용하는 것은 SQLAlchemy 데이터베이스를 사용하기 위해 따라야 할 규칙이다. 정해진 규칙대로 사용하면 되지만 여기서 `autocmmit=False` 부분은 주의한다. `autocommit=False`로 설정하면 데이터를 변경했을 때 commit 이라는 사인을 주어야만 실제 저장이 된다. 만약 `autocommit=True`로 설정할 경우에는 commit이라는 사인이 없어도 즉시 데이터베이스에 변경사항이 적용된다. 그리고 `autocommit=False`인 경우에는 데이터를 잘못 저장했을 경우 rollback 사인으로 되돌리는 것이 가능하지만 `autocommit=True`인 경우에는 commit이 필요 없는 것처럼 rollback도 동작하지 않는다는 점에 주의해야 한다.

`create_engine`은 커넥션 풀을 생성한다. 커넥션 풀이란 데이터베이스에 접속하는 객체를 일정 갯수만큼 만들어 놓고 돌려가며 사용하는 것을 말한다.(커넥션 풀은 데이터베이스에 접속한느 세션 수를 제어하고, 또 세션 접속에 소요되는 시간을 줄이고자 하는 용도로 사용한다.)
그리고 `declarative_base` 함수에 의해 반환된 `Base` 클래스는 데이터베이스 모델을 구성할 때 사용되는 클래스이다.


## 모델 만들기

질문 답변 게시판에 쓸 모델을 만들어본다. 질문 답변 게시판이므로 질문과 답변에 해당하는 모델이 있어야 한다.

### 모델 속성 구상하기

질문 모델에는 다음 속성이 필요할 것이다.

- 질문 모델 속성

| 속성명  | 설명 |
| ------- | ---- |
| id      |  질문 데이터의 고유 번호    |
| subject |  질문 제목    |
| content|질문 내용|
|create_date|  질문 작성 일시    |

그리고 답변 모델은 다음과 같은 속성이 필요하다.

- 답변 모델 속성

| 속성명      | 설명                                                                                                 |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| id          | 답변 데이터의 고유 번호                                                                              |
| question_id | 질문 데이터의 고유 번호(어떤 질문에 달린 답변인지 알아야 하므로 질문 데이터의 고유 번호가 필요하다.) |
| content     | 답변 내용                                                                                            |
| create_date | 답변 작성 일시                                                                                       |


### 질문 모델 생성하기

이렇게 구상한 속성을 바탕으로 모델을 정의해 본다. 먼저 모델을 정의하기 위한 models.py 파일을 생성하고 질문 모델인 `Question` 클래스를 다음과 같이 작성해 본다.

```python
from sqlalchemy import Column, Integer, String, Text, DateTime
from database import Base

class Question(Base):
	__tablename__ = "question"
	
	id = Column(Integer, primary_key=True)
	subject = Column(String, nullable=False)
	content = Column(Text, nullable=False)
	create_date = Column(DateTime, nullable=False)
```

`Question` 과 같은 모델 클래스는 앞서 database.py에서 정의한 `Base` 클래스를 상속하여 만들어야 한다. `__tablename__`은 모델에 의해 관리되는 테이블의 이름을 뜻한다. `Question` 모델은 고유 번호(id), 제목(subject), 내용(content), 작성일시(create_date) 속성으로 구성했으며, 각 속성은 `Column`으로 생성했다. 

`Column()` 괄호 안의 첫 번쨰 인수는 데이터 타입을 의미한다. 데이터 타입은 속성에 저장할 데이터의 종류를 결정한다. `Integer`는 고유 번호와 같은 숫자값에 사용하고, `String`은 제목처럼 글자 수가 제한된 텍스트에 사용한다. 글 내용처럼 글자 수를 제한할 수 없는 텍스트는 `Text`를 사용한다. 작성 일시는 날짜 타입인 `DateTime`을 사용했다.

`Column`에는 데이터 타입 외에 다음과 같은 속성을 추가로 설정할 수 있다.

- primary_key
	- id 속성에 설정한 primary_key는 id 속성을 기본 키(Primary Key)로 만든다. 기본 키는 데이터베이스에서 중복된 값을 가질 수 없게 만드는 설정이다. id는 모델에서 각 데이터를 구분하는 유일한 값으로 중복되면 안되므로 기본키로 지정했다.
- nullable
	- nullable은 속성에 값을 지정할 때 null 값을 허용할지의 여부이다. nullable을 따로 설정하지 않으면 해당 속성은 기본으로 null 값을 허용한다. 따라서 속성에 null 값을 허용하지 않으려면 `nullable=False`로 설정해야 한다.


### 답변 모델 생성하기

이어서 답변 모델에 해당하는 Answer 클래스도 만들어 본다.

```python
from sqlalchemy import Column, Integer, String, Text, DateTime, ForeignKey
from sqlalchemy.orm import relationship
from database import Base

class Question(Base):
	__tablename__ = "question"
	
	id = Column(Integer, primary_key=True)
	subject = Column(String, nullable=False)
	content = Column(Text, nullable=False)
	create_date = Column(DateTime, nullable=False)
	
class Answer(Base)
	__tablename__ = "answer"
	
	id = Column(Integer, primary_key=True)
	content = Column(Text, nullable=False)
	create_date = Column(DateTime, nullable=False)
	question_id = Column(Integer, ForeignKey("question.id"))
	question = relationship("Question", backref="answer")
```


답변 모델에서 id와 `content`, `create_date` 속성은 질문 모델의 id, `content`, `create_date`와 의미와 목적이 같다. 다른 속성은 `question_id`와 `question`인데 두 속성이 왜 필요하고 어떤 의미를 갖는지 알아본다.

- question_id
	- ```python
	  question_id = Column(Integer, ForeignKey("question.id"))
	  ```

question_id 속성은 답변을 질문과 연결하기 위해 추가한 속성이다. 답변은 어떤 질문에 대한 답변인지 알아야 하므로 질문의 id 속성이 필요하다. 그리고 모델을 서로 연결할 때에는 위와 같이 `ForeignKey`를 사용해야 한다.

> 데이터베이스에서는 기존 모델과 연결된 속성을 외부 키(foreign key)라고 한다.

`ForeignKey`의 첫 번째 파라미터 `question.id`는 question 테이블의 id 컬럼을 의미한다. 즉, Answer 모델의 question_id 속성은 question 테이블의 id 컬럼과 연결된다는 뜻이다.

- question
	- ```python
	  question = relationship("Question", backref="answer")
	  ```

그 다음 question 속성은 답변 모델에서 질문 모델을 참조하기 위해 추가했다. 위와 같이 `relationship`으로 question 속성을 생성하면 답변 객체(예: answer)에서 연결된 질문의 제목을 `answer.question.subject` 처럼 참조할 수 있다.

`relationship`의 첫 번째 파라미터는 참조할 모델명이고 두 번째 `backref` 파라미터는 역참조 설정이다. 역참조란 쉽게 말해 질문에서 답변을 거꾸로 참조하는 것을 의미한다. 한 질문에는 여러 개의 답변이 달릴 수 있는데 역참조는 이 질문에 달린 답변들을 참조할 수 있게 한다. 예를 들어 어떤 질문에 해당하는 객체가 `a_question`이라면 `a_question.answers`와 같은 코드로 해당 질문에 달린 답변들을 참조할 수 있다.

SQLAlchemy에서 제공하는 속성은 위에서 소개한 것 외에도 많이 있다. 자세한 내용은 아래의 URL을 참고하면 된다.

> -[https://docs.sqlalchemy.org/en/13/core/type_basics.html](https://docs.sqlalchemy.org/en/13/core/type_basics.html)


## 모델을 이용해 테이블 자동으로 생성하기

모델을 구상하고 생성했으므로 SQLAlchemy의 alembic을 이용해 데이터베이스 테이블을 생성해 본다.

alembic은 SQLAlchemy로 작성한 모델을 기반으로 데이터베이스를 쉽게 관리할 수 있게 도와주는 도구이다. 예를 들어 models.py 파일에 작성한 모델을 이용하여 테이블을 생성하고 변경할 수 있다.


### alembic 설치

```bash
pip install alembic 
# or
uv add alembic 
```


### alembic 초기화

alembic이 잘 설치되었다면 이제 alembic 초기화 작업을 진행해야 한다.

```bash
(.venv) kimseoyeon:fastapi/ (main✗) $ alembic init migrations                                                               [10:21:45]
  Creating directory /Users/kimseoyeon/practice/fastapi/migrations ...  done
  Creating directory /Users/kimseoyeon/practice/fastapi/migrations/versions ...  done
  Generating /Users/kimseoyeon/practice/fastapi/migrations/script.py.mako ...  done
  Generating /Users/kimseoyeon/practice/fastapi/migrations/env.py ...  done
  Generating /Users/kimseoyeon/practice/fastapi/migrations/README ...  done
  Generating /Users/kimseoyeon/practice/fastapi/alembic.ini ...  done
  Please edit configuration/connection/logging settings in /Users/kimseoyeon/practice/fastapi/alembic.ini before proceeding.
```

그러면 프로젝트 디렉토리 하위에 migrations라는 디렉토리와 alembic.ini 파일이 생성된다. migrations 데릭토리는 alembic 도구를 사용할 때 생성되는 리비전 파일들을 저장하는 용도로 사용되고 alembic.ini 파일은 alembic 환경 설정 파일이다.

> alembic을 이용하여 테이블 생성 또는 변경할 때마다 작업 파일이 생성되는데 이 작업 파일을 리비전 파일이라고 한다. 그리고 이 리비전 파일은 migrations 디렉토리에 저장된다.

이어서 alembic.ini 파일을 수정한다.

```ini
(... 생략 ...)
sqlalchemy.url = sqlite:///./myapi.db
(... 생략 ...)
```

> alembic이 상요할 데이터베이스의 접속주소를 설정했다.

그리고 migrations 디렉토리의 env.py도 다음과 같이 수정한다.

```python
(... 생략 ...)
import models
(... 생략 ...)
# add your model's MetaData object here
# for 'autogenerate' support
# from myapp import mymodel
# target_metadata = mymodel.Base.metadata
target_metadata = models.Base.metadata
(... 생략 ...)
```


### 리비전 파일 생성하기

그리고 터미널에서 `alembic revision --autogenerate` 명령을 수행한다.

```bash
(.venv) kimseoyeon:fastapi/ (main✗) $ alembic revision --autogenerate                                                       [10:26:02]
INFO  [alembic.runtime.migration] Context impl SQLiteImpl.
INFO  [alembic.runtime.migration] Will assume non-transactional DDL.
INFO  [alembic.autogenerate.compare] Detected added table 'question'
INFO  [alembic.autogenerate.compare] Detected added table 'answer'
  Generating /Users/kimseoyeon/practice/fastapi/migrations/versions/28ca48a12485_.py ...  done
```

그러면 `migrations/versions` 디렉토리에 `28ca48a12485_.py`와 같은 리비전 파일이 생성된다. 리비전(revision)이란 생성된 `28ca48a12485_.py` 파일에서 `.py` 확장자를 제외한 `28ca48a12485_`와 같은 버전 번호를 가리킨다. 리비전은 `alembic revision --autogenerate` 명령을 수행할 때 무작위로 만들어진다.

> 리비전 파일에는 테이블을 생성 또는 변경하는 실행문들이 들어 있다.

### 리비전 파일 실행하기

`alembic revision --autogenerate` 명령으로 만들어진 리비전 파일을 `alembic upgrade head` 명령으로 실행한다.

```bash
(.venv) kimseoyeon:fastapi/ (main✗) $ alembic upgrade head                                                                  [10:27:08]
INFO  [alembic.runtime.migration] Context impl SQLiteImpl.
INFO  [alembic.runtime.migration] Will assume non-transactional DDL.
INFO  [alembic.runtime.migration] Running upgrade  -> 28ca48a12485, empty message
```

이 과정에서 데이터베이스에 모델에 정의한 question과 answer라는 이름의 테이블이 생성된다. 프로젝트 루트 디렉토리에 myapi.db 파일이 생성되었을 것이다. myapi.db가 바로 SQLite 데이터베이스의 데이터 파일이다.

### albemic 없이 테이블 생성하기

main.py 파일에 다음의 문장을 삽입하면 FastAPI 실행시 필요한 테이블들이 모두 생성된다.

```python
import models
from database import engine

models.Base.metadata.create_all(bind=engine)
```

매우 간단한 방법이지만 데이터베이스에 테이블이 존재하지 ㅇ낳을 경우에만 테이블을 생성한다. 한 번 생성된 테이블에 대한 변경 관리를 할 수는 없다. 


## 생성된 테이블 살펴보기

myapi.db 데이터 파일에 정말로 question과 answer 테이블이 생성되었는지 확인해 본다. 이를 위해 SQLite의 GUI 도구인 DB Browser for SQLite를 사용해 본다.

### DB Browser for SQLite 설치하기

[https://sqlitebrowser.org/dl](https://sqlitebrowser.org/dl) 에 접속한 다음 DB Browser for SQLite(이하 DB 브라우저) 설치 파일(standard installer)을 내려받아 설치를 진행한다.

> 자신의 운영체제에 맞는 설치 파일을 내려받아야하며, 설치 중 바로 가기(shortcuts)를 생성하는 옵션을 추가해야 쉽게 실행할 수 있다.

![](https://i.imgur.com/ZBDGT2V.png)

### DB 브라우저에서 myapi.db 열기

윈도우 바탕화면이나 프로그램 메뉴에서 방금 설치한 DB 브라우저를 실행하고 메뉴에서 [파일 → 데이터베이스 열기]를 선택한다. 그리고 앞선 실습에서 생성한 `projects/myapi/myapi.db` 데이터베이스 파일을 선택하고 `<열기>`를 누른다.

![](https://i.imgur.com/AJySdBa.png)

테이블 목록을 보면 question, answer 테이블이 생성되었음을 확인할 수 있다.

> alembic_version 테이블은 alembic 도구가 데이터베이스를 변경·관리하려고 사용하는 테이블이므로 신경 쓰지 않아도 된다.


- 나는 DBeaver를 사용중이어서 해당 GUI에서 확인했다.

![](https://i.imgur.com/dnpoxHG.png)


> 출처: [https://wikidocs.net/175967](https://wikidocs.net/175967)