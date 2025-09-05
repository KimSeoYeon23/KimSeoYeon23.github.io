---
layout: post
title: "SQLAlchemy"
date: 2025-09-05 09:24:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## SQLAlchemy

> SQLAlchemy는 Python에서 사용되는 강력하고 유연한 SQL 툴킷 및 객체 관계 매핑(Object-Relational Mapping, ORM) 라이브러리이다. 이 라이브러리는 데이터베이스와의 상호 작용을 쉽고 효율적으로 만들어 주며, SQL과 객체 지향 프로그래밍 사이의 간격을 줄여 준다.

## 주요 특징

- **ORM 레이어**: Python 클래스를 데이터베이스 테이블에 매핑하고, Python 객체를 해당 테이블의 행과 동기화한다. 이를 통해 SQL 쿼리를 직접 작성하지 않고도 데이터베이스 작업을 할 수 있다.
- **SQL 표현 언어**: 복잡한 SQL 쿼리를 Python 코드로 작성할 수 있는 선언적 방식을 제공한다. 이를 통해 데이터베이스와의 상호작용을 보다 세밀하게 제어할 수 있다.
- **데이터페이스 독립성**: SQLAlchemy는 다양한 데이터베이스 엔진을 지원한다. SQLite, PostgreSQL, MySQL, Oracle, Microsoft SQL Seerver 등과 같은 주요 데이터베이스에 모두 호환된다.
- **트랜잭션 관리**: 세선 기반의 작업을 통해 트랜잭션 관리를 쉽게 할 수 있으며, 데이터베이스 연결과 트랜잭션의 생명 주기를 효율적으로 관리한다.
- **유연성 및 확장성**: 다양한 사용 사례와 요구 사항에 맞게 SQLAlchemy를 확장하고 맞춤화할 수 있다.

### 예제 코드

```python
from sqlalchemy import create_engine, Column, Integer, String, MetaData, Table

# SQLite 데이터베이스에 연결 및 메타데이터 객체 생성
engine = create_engine('mysql+pymysql://<USERNAME>:<PASSWORD>@{HOST}:{PORT}/<DBNAME>', echo=True)
metadata = MetaData()

# 테이블 정의 및 생성

users = Table('users', meatdata,
			Column('id', Integer, primary_key=True),
			Column('name', String),
			Column('age', Integer)
		)
metadata.create_all(engine)
```

SQLAlchemy는 그 유연성과 강력한 기능으로 인해 Python 개발자들 사이에서 데이터베이스 작업에 대한 선호도가 높은 라이브러리이다. 데이터베이스 작업을 Pythonic하게 만들어 주며, 복잡한 쿼리와 데이터베이스 상호작용을 보다 쉽게 할 수 있게 도와준다.


## SQLAlchemy 기본 객체


### engine

데이터베이스와의 연결을 관리 (URL 형식의 DB 접근 주소를 필요로 함 (`create_engine`))

```python
from sqlalchemy import create_engine

# 1. engein 생성
engine = create_engine(
	'mysql+pymysql://<USERNAME>:<PASSWORD>@{HOST}:{PORT}/<DBNAME>',
	echo=True,
	pool_size=2,
	pool_recycle=3600,
	max_overflow=0,
	pool_timeout=3,
	isolation_level='READ UNCOMMITTED'
)
```

**create_engine**
- **echo**
	- log 기록
- **pool_size**
	- 연결 풀 내에서 도시에 유지할 연결의 최대 수 (0: 무제한)
- **pool_recycle**
	- MySQL/MariaDB의 고정된 기간 동안 유휴 상태였던 연결에 대해 자동 연결 종료 (기본갑 8시간) 자동으로 삭제 처리 되려면, 명시적인 값 설정 필요
- **max_overflow**
	- 풀에 있는 연결의 최대 추가 갯수
- **pool_timeout**
	- 연결 풀에서 연결을 가져오기 위해 대기할 최대 시간
- **isolation_level**
	- 트랜잭션 격리 수준 설정

**isolation 관련**
- `create_engine.isolation_level`의 인수를 통한 설정 방법 외에도 `Connection.execution.options.isolation_elvel`를 통한, 연결 마다의 설정도 가능
- `READ COMMITED`, `READ UNCOMMITTED`, `REPEATABLE READ`, `SERIALIZABLE`, `AUTOCOMMIT` 레벨들이 있음

**engine.dispose()**
- engine에서 가진 connection pool 자체를 다 종료한다.



### Base

`Base` 클래스의 역할은 모든 ORM 모델의 기반으로 `declarative_base()` 함수를 통해 호출하여 생성되며 **모든 모델은 이 `Base` 클래스를 상속 받아야 한다.**
`Base`를 상속받은 각 모델은 테이블의 구조(이름, 컬럼, 데이터 타입 등)를 정의한다.

```python
from sqlalchemy.orm import declarative_base
from sqlalchemy import Column, Integer, String

# 2. Base: 모든 모델의 기본 클래스
Base = declarative_base()

class User(Base):
	__tablename__ = "users"
	id = Column(Integer, primary_key=True, autoincrement=True)
	name = Column(String(50), nullable=False)
	age = Column(Integer, nullable=False)
```


### MetaData

SQLAlchemy에서 데이터베이스의 스키마(테이블, 컬럼, 인덱스, 제약조건, 관계 등) 정보를 저장하고 관리하는 객체이다. `Base`를 상속받아 생성된 모델들의 정보를 담고 있다. `Base` 클래스가 생성될 때 자동으로 `MetaData` 객체도 생성되며, 모든 모델 클래스들이 `MetaData`에 등록된다. 이를 통해 전체 데이터베이스 구조를 관리할 수 있게 된다.

```python
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Colun, Integer, String

# 2. Base: 모든 모델의 기본 클래스
Base = declarative_base()

# 3.1 Base.metamdata: 각 모델에 대한 메타 정보
print(Base.metadata.tables)   # 테이블 정보 출력

# immutabledict({
	 # 'users': 
		 # Table('users', 
			 # MetaData(bind=None), 
			 # Column('id', Integer(), table=<users>, primary_key=True, nullable=False), 
			 # Column('name', String(), table=<users>), 
			 # Column('age', Integer(), table=<users>), schema=None) 
 # }) 
 
 # 3.2 Base.metadata의 정보를 바탕으로 engine에 연결된 DB에 테이블 생성
 Base.metadata.create_all(engine)
```


### sessionmaker, Session

세션은 데이터베이스 엔진과 연결되어 해당 DB의 트랜잭션을 관리하고, 데이터베이스 간의 변경사항을 추적하는 중요한 역할을 한다. `sessionmaker`를 사용해 **session 팩토리** 생성한다.
최종 **세션 객체 `Session()`을 생성**하고, DB에 대한 조회, 삽입, 갱신, 삭제 등을 수행한다.

```python
from sqlalchemy.orm import sessionmaker

# 1. 데이터베이스 엔진 생성 
engine = create_engine('sqlite:///example.db') 

# 2. Base를 이용한 모델 정의와 3. meta를 이용한 테이블 생성은 생략

 # 4.1 sessionmaker를 사용해 세션 팩토리 생성 
 Session = sessionmaker(bind=engine) 

 # 4.2 세션 객체 생성 - DB에 대한 쿼리, 삽입, 갱신 등을 수행 
 session = Session()
```


### session의 재사용

Session은 내부적으로 데이터베이스 연결을 풀(connection pool)에서 가져와 사용하고, 작업이 끝나면 풀에 반환한다.

**Session.close()** 란
- pool에 있는 세션을 사용하다가, 다시 반환하는 것이다. 
- ORM 객체 해제: 세션이 관리하고 있는 ORM 객체에 대한 "관리 상태"를 해제하여, 세션이 해당 객체의 변경 사항을 추적하지 않음을 의미한다.
- 세션 상태 초기화: Session은 내부적으로 사용된 리소스와 캐시를 정리한다.
- session.close()를 하더라도 객체는 여전히 존재하며, 필요할 때 다시 사용 가능하다.
- session.close()를 호출 후 세션 객체를 재사용하여 새 쿼리를 실행하거나 트랜잭션을 시작한다면 세션은 pool에서 새 연결을 가져와 데이터베이스와 통신한다.

즉 세션은 DB와의 연결을 완전히 닫는 것이 아닌 재사용 가능한 상태로 만든다는 것이다.

> 만약 connection pool까지 종료하려면?
> `engine.dispose()`


```python
# 세션 생성
session = Session()

# 데이터베이스 작업 수행
user = session.query(User).first()

# 세션 닫기
session.close()

# 세션을 다시 사용하여 새 쿼리 수행
another_user = session.query(User).first()   # 재사용 가능
```

> 출처: [https://wikidocs.net/226764](https://wikidocs.net/226764), [https://yubi5050.tistory.com/317](https://yubi5050.tistory.com/317)