---
layout: post
title: "싱글톤(Singleton)"
date: 2025-09-11 09:41:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 싱글톤(Singleton)

Singleton 디자인 패턴은 클래스가 하나의 인스턴스만을 갖도록 하고, 그 인스턴스를 시스템 전여겡서 액세스할 수 있도록 하는 패턴이다. Python에서 싱글톤 클래스가 하나의 인스턴스를 갖도록 하기 위해서 `__init__()` 함수에서 객체 생성을 금지시키게 되는데, 일반적으로 `__init__` 안에서 `raise Exception()`을 사용하게 된다. 싱글톤에서 생성되는 하나의 인스턴스는 실제 클래스 메서드를 사용하여 아래 예제의 `get_instance()`와 같이 캐시된 `_instance`가 없는 경우 새로 생성하고, 이미 있는 경우 그 `_instance` 필드값을 리턴하는 방식을 사용한다.

```python
class Singleton:
	_instance = None
	
	def __init__(self):
		raise Exception("Unable to create new instance:)
	
	@classmethod
	def get_instance(cls):
		if cls._instance is None:
			cls._instance = cls.__new__(cls)
		return cls._instance
```


## 싱글톤 사용하기

Singleton 인스턴스르 사용하기 위해서는, 클래스 객체를 개별적으로 생성하는 대신 Singleton 클래스의 싱글톤 생성 클래스 메서드(`get_instance`)를 사용한다. 예를 들어, 아래 예제에서 `Singleton.get_instance()`를 호출하여 싱글톤 인스턴스를 가져온 후, `show_time()`과 같은 인스턴스 메서드를 호출한다.

```python
import datetime

class Singleton:
	_instance = None
	
	def __init__(self):
		raise Exception("Unable to create new instance:)
	
	@classmethod
	def get_instance(cls):
		if cls._instance is None:
			cls._instance = cls.__new__(cls)
		return cls._instance
	
	def show_time(self):
		now = datetime.datetime.now()
		print(now.strftime("%Y-%m-%d %H:%M:%S"))
		
inst = Singleton.get_instance()
inst.show_time()
```


## 싱글톤 파생클래스 사용

Singleton 클래스를 생성한 후, 여기서 클래스를 파생하는 방식으로 싱글톤 패턴을 사용할 수 있다. 파생클레스에서 싱글톤 객체를 생성하기 위해서는, 부모클래스의 `get_instance()`를 호출하여 사용하고, 부모 혹은 파생클래스의 인스턴스 메서드를 호출하면 된다. 아래 예제는 SIngleton 부모 클래스에서 `MyClass` 파생클래스를 생성하고, 사용한 예를 표현한 것이다.

```python
class MyClass(Singleton):
	def start(self):
		print("START")

my = MyClass.get_instance()
my.start()
```

그리고 (부모 클래스의 `get_instance()`를 사용하는 대신) 파생클래스에서 `get_instance()` 클래스 메서드를 재정의(overried)하여 사용할 수도 있는데, 이는 파생클래스의 멤버를 초기화하는데 유용하다.


> 출처: [http://pythonstudy.xyz/python/article/518-%EC%8B%B1%EA%B8%80%ED%86%A4-Singleton](http://pythonstudy.xyz/python/article/518-%EC%8B%B1%EA%B8%80%ED%86%A4-Singleton)