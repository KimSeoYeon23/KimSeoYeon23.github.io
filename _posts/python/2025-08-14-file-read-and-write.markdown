---
layout: post
title: "파일 읽고 쓰기"
date: 2025-08-14 10:31:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}


## 파일 생성하기

다음 코드를 IDLE 에디터로 작성하여 실행해 본다.

```python
f = open("새파일.txt", 'w')
f.close()
```

프로그램을 실행한 디렉터리에 새로운 파일이 하나 생성된 것을 확인할 수 있을 것이다. 파일을 생성하기 위해 파이썬 내장 함수 open을 사용했다. open 함수는 다음과 같이 '파일 이름'과 '파일 열기 모드'를 입력값으로 받고 결괏값으로 파일 객체를 리턴한다.

```python
파일_객체 = open(파일_이름, 파일_열기_모드)
```

파일 열기 모드에는 다음과 같은 것들이 있다.

| 파일열기모드 | 설명                                                         |
| ------------ | ------------------------------------------------------------ |
| r            | 읽기 모드: 파일을 읽기만 할 때 사용한다.                     |
| w            | 쓰기 모드: 파일에 내용을 쓸 때 사용한다.                     |
| a            | 추가 모드: 파일의 마지막에 새로운 내용을 추가할 때 사용한다. |

파일을 쓰기 모드로 열면 해당 파일이 이미 존재할 경우 원래 있던 내용이 모두 사라지고 해당 파일이 존재하지 않으면 새로운 파일이 생성된다. 위 예에서는 디렉터리에 파일이 없는 상태에서 '새파일.txt' 파일을 쓰기 모드인 'w'로 열었기 때문에 '새파일.txt'라는 이름의 새로운 파일이 현재 디렉터리에 생성되었다.

만약 '새파일.txt' 파일을 `C:/doit` 디렉터리에 생성하고 싶다면 다음과 같이 작성해야 한다.

```python
f = open("C:/doit/새파일.txt", "w")
f.close()
```

위 예에서 f.close()는 열려 있는 파일 객체를 닫아 주는 역할을 한다. 사실 이 문장은 생략해도 된다 .프로그램을 종료할 때 파이썬 프로그램이 열려 있는 파일의 객체를 자동으로 닫아 주기 때무니다. 하지만 close()를 사용해서 열려 있는 파일을 직접 닫아 주는 것이 좋다. 쓰기 모드로 열었던 파일을 닫지 않고 다시 사용하려고 하면 오류가 발생하기 때문이다.

> **파일 경로와 슬래시(`/`**
> 파이썬 코드에서 파일 경로를 표시할 때 `"C:/doit/새파일.txt"`처럼 슬래시(/)를 사용할 수 있다. 만약 역슬래시(`\`)를 사용한다면 `"C:\\doit\\새파일.txt"`처럼 역슬래시를 2개 사용하거나 `r"C:\doit\새파일.txt"`와 같이 문자열 앞에 r 문자(raw string)를 덧붙여 사용해야 한다. 왜냐하면 `"C:\note\test.txt"`처럼 파일 경로에 `\n`과 같은 이스케이프 문자가 있을 경우, 줄바꿈 문자로 해석되어 의도했던 파일 경로와 달라지기 때문이다.


## 파일을 쓰기 모드로 열어 내용 쓰기

위 예에서는 파일을 쓰기 모드로 열기만 했을 뿐, 정작 아무것도 쓰지는 않았다. 이번에는 문자열 데이터를 파일에 직접 써 본다.

```python
f = open("C:/doit/새파일.txt", "w")
for i in range(1, 11):
	data = "%d번째 줄입니다.\n" % i
	f.write(data)
f.close()
```

위 프로그램을 다음과 비교해 본다.

```python
for i in range(1, 11):
	data = "%d번째 줄입니다.\n" % i
	print(data)
```

두 프로그램의 다른 점은 data를 출력하는 방법이다. 첫 번째는 모니터 화면 대신 파일에 데이터를 적는 방법, 두 번째는 우리가 계속 사용해 왔던 모니터 화면에 데이터를 출력하는 방법이다. 두 방법의 차이점은 print 함수 대신 파일 객체 f의 write 함수를 사용한 것 말고는 없으므로 바로 눈에 들어올 것이다.

이제 명령 프롬프트 창에서 첫 번째 예제를 실행해 본다.

```bash
~/practice/python_crawling » python write_data.py                                                                         130 ↵ kimseoyeon@Yeons-MackBook
(.venv) --------------------------------------------------------------------------------------------------------------------------------------------------
~/practice/python_crawling »     
```

이 프로그램을 실행한 디렉터리를 살펴보면 '새파일.txt' 파일이 생성된 것을 볼 수 있다. 파일 안에는 어떤 내용이 담겨 있는지 확인해 본다.

![](https://i.imgur.com/zllfJVW.png)

모니터 화면에 출력될 내용이 고스란히 파일에 들어 있는 것을 볼 수 있다.


## 파일을 읽는 여러 가지 방법

파이썬에는 파일을 읽는 방법이 여러 가지 있다. 


### readline 함수 이용하기

첫 번째는 readline 함수를 이용하는 것이다.

```python
f = open("C:/doit/새파일.txt", "r")
line = f.readline()
print(line)
f.close()
```

위는 '새파일.txt' 파일을 읽기 모드로 연 후 readline()을 사용해서 파일의 첫 번째 줄을 읽어 출력하는 예제이다. 앞에서 만든 새파일.txt 파일을 수정하거나 지우지 않았다면 위 프로그램을 실행했을 때 새파일.txt 파일의 가장 첫 번째 줄이 화면에 출력될 것이다.

```text
1번째 줄입니다.
```

만약 모든 줄을 읽어 화면에 출력하고 싶다면 다음과 같이 작성하면 된다.

```python
f = open("C:/doit/새파일.txt", "r")
while True:
	line = f.readline()
	if not line: break
	print(line)
f.close()
```

`while True:` 무한 루프 안에서 `f.readline()`을 사용해 파일을 계속 한 줄씩 읽어 들인다. 만약 더 이상 읽을 줄이 없으면 break를 수행한다(readline()은 더 이상 읽을 줄이 없을 경우, 빈 문자열('')을 리턴한다).

앞의 프로그램을 다음과 비교해 본다.

```python
while True:
    data = input()
    if not data: break
    print(data)
```

위 예는 사용자의 입력을 받아 그 내용을 출력하는 경우이다. 파일을 읽어서 출력하는 예제와 비교해 본다. 입력을 받는 방식만 다르다는 것을 바로 알 수 있을 것이다. 두 번째 예는 키보드를 사용한 입력 방법, 첫 번째 예는 파일을 사용한 입력 방법이다.

### readlines 함수 사용하기

두 번째 방법은 readlines 함수를 사용하는 것이다. 

```python
# readlines.py
f = open("C:/doit/새파일.txt", 'r')
lines = f.readlines()
for line in lines:
    print(line)
f.close()
```

readlines 함수는 파일의 모든 줄을 읽어서 각각의 줄을 요소로 가지는 리스트를 리턴한다. 따라서 위 예에서 lines는 리스트 `["1번째 줄입니다.\n", "2번째 줄입니다.\n", ..., "10번째 줄입니다.\n"]`가 된다. `f.readlines()`는 `f.readline()`와 달리 s가 하나 더 붙어 있다는 것에 유의한다.

> **줄 바꿈(`\n`) 문자 제거하기**
> 
> 파일을 읽을 때 줄 끝의 줄 바꿈(`\n`) 문자를 제거하고 사용해야 할 경우가 많다. 다음처럼 strip 함수를 사용하면 줄 바꿈 문자를 제거할 수 있다.
```python
f = open("C:/doit/새파일.txt", 'r')
lines = f.readlines()
for line in lines:
    line = line.strip()  # 줄 끝의 줄 바꿈 문자를 제거한다.
    print(line)
f.close()
```

### read 함수 사용하기

세 번째는 read 함수를 사용하는 방법이다. 

```python
# read.py
f = open("C:/doit/새파일.txt", 'r')
data = f.read()
print(data)
f.close()
```

`f.read()`는 파일의 내용 전체를 문자열로 리턴한다. 따라서 위 예의 data는 파일의 전체 내용이다.

### 파일 객체를 for 문과 함께 사용하기

네 번째는 파일 객체를 for 문과 함께 사용하는 방법이다.

```python
# read_for.py
f = open("C:/doit/새파일.txt", 'r')
for line in f:
    print(line)
f.close()
```

파일 객체(f)는 기본적으로 위와 같이 for 문과 함께 사용하여 파일을 줄 단위로 읽을 수 있다.

## 파일에 새로운 내용 추가하기

쓰기 모드('w')로 파일을 열 때 이미 존재하는 파일을 열면 그 파일의 내용이 모두 사라지게 된다. 하지만 원래 있던 값을 유지하면서 단지 새로운 값만 추가해야 할 경우도 있다. 이런 경우에는 파일을 추가 모드('a')로 열면 된다. IDLE 에디터로 다음 소스 코드를 작성해 본다..

```python
# add_data.py
f = open("C:/doit/새파일.txt",'a')
for i in range(11, 20):
    data = "%d번째 줄입니다.\n" % i
    f.write(data)
f.close()
```

위는 새파일.txt 파일을 추가 모드('a')로 열고 write를 사용해서 결괏값을 기존 파일에 추가해 적는 예이다. 여기에서 추가 모드로 파일을 열었기 때문에 새파일.txt 파일이 원래 가지고 있던 내용 바로 다음부터 결괏값을 적기 시작한다.

다음과 같이 작성한 코드를 실행해 보자.

```no-highlight
C:\Users> cd C:\doit
C:\doit> python add_data.py
C:\doit>
```

새파일.txt 파일을 열어 보면 원래 있던 내용 뒤에 새로운 내용이 추가된 것을 확인할 수 있다.

![](https://i.imgur.com/1CxwRsw.png)


## with 문과 함께 사용하기

지금까지 살펴본 예제를 보면 항상 다음과 같은 방식으로 파일을 열고 닫은 것을 알 수 있다.

```python
f = open("foo.txt", 'w')
f.write("Life is too short, you need python")
f.close()
```

파일을 열면(open) 항상 닫아(close) 주어야 한다. 이렇게 파일을 열고 닫는 것을 자동으로 처리할 수 있다면 편리하지 않을까? 파이썬의 with 문이 바로 이런 역할을 해 준다. 다음 예는 with 문을 사용해서 위 예제를 다시 작성한 모습이다.

```python
# file_with.py
with open("foo.txt", "w") as f:
    f.write("Life is too short, you need python")
```

위와 같이 with 문을 사용하면 with 블록(with 문에 속해 있는 문장)을 벗어나는 순간, 열린 파일 객체 f가 자동으로 닫힌다.

> 출처: [https://wikidocs.net/26](https://wikidocs.net/26)