---
layout: post
title: "FastAPI 파일 요청"
date: 2025-09-03 09:33:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## FastAPI의 파일 요청

## 파일 요청

`File`을 사용하여 클라이언트가 업로드할 파일들을 정의할 수 있다.

> 업로드된 파일을 전달받기 위해 먼저 `python-multipart`를 설치해야 한다.
> 예시) `pip install python-multipart`
> 업로드된 파일들은 "폼 데이터"의 형태로 전송되기 때문에 이 작업이 필요하다.


## `File` 임포트

`fastapi`에서 `File`과 `UploadFile`을 임포트한다.

```python
from typing import Annotated
from fastapi import FastAPI, File, UploadFile

app = FastAPI()

@app.post("/files/")
async def create_file(file: Annotated[bytes, File()]):
	return {"file_size": len(file)}
	
@app.post("/uploadfile/)
async def create_upload_file(file: UploadFile):
	return {"filename": file.filename}
```



## `File` 매개변수 정의

 `Body` 및 `Form` 과 동일한 방식으로 파일의 매개변수를 생성한다.


```python
from typing import Annotated
from fastapi import FastAPI, File, UploadFile

app = FastAPI()

@app.post("/files/")
async def create_file(file: Annotated[bytes, File()]):
	return {"file_size": len(file)}
	
@app.post("/uploadfile/)
async def create_upload_file(file: UploadFile):
	return {"filename": file.filename}
```

`File`은 `Form`으로부터 직접 상속된 클래스이다. 하지만 `fastapi`로부터 `Query`, `Path`, `File` 등을 임포트 할 때, 이것은 특별한 클래스들을 반환하는 함수라는 것을 기억해야 한다.

`File`의 본문을 선언할 때, 매개변수가 쿼리 매개변수 또는 본문(JSON) 매개변수로 해석되는 것을 방지하기 위해 `File`을 사용해야 한다.

파일들은 "폼 데이터"의 형태로 업로드 된다. 경로 작동 함수의 매개변수를 `bytes`로 선언하는 경우 **FastAPI**는 파일을 읽고 `bytes` 형태의 내용을 전달한다. 이것은 전체 내용이 메모리에 저장되는 것을 의미한다는 걸 염두해야 한다. 이는 작은 크기의 파일들에 적합하다.

어떤 경우에는 `UploadFile`을 상요하는 것이 더 유리하다.


## `File` 매개변수와 `UploadFile`

`File` 매개변수를 `UploadFile` 타입으로 정의한다.

```python
from typing import Annotated
from fastapi import FastAPI, File, UploadFile

app = FastAPI()

@app.post("/files/")
async def create_file(file: Annotated[bytes, File()]):
	return {"file_size": len(file)}
	
@app.post("/uploadfile/)
async def create_upload_file(file: UploadFile):
	return {"filename": file.filename}
```

`UploadFile`을 사용하는 것은 `bytes`과 비교해 다음과 같은 장점이 있다.

- "스풀 파일"을 사용한다.
	-  최대 크기 제한까지만 메모리에 저장되며, 이를 초과하는 경우 디스크에 저장된다.
- 따라서 이미지, 동영상, 큰 이진코드와 같은 대용량 파일들을 많은 메모리를 소모하지 않고 처리하기에 적합하다.
- 업로드 된 파일의 메타데이터를 얻을 수 있다.
- file-like `async` 인터페이스를 갖고 있다.
- file-like object를 필요로하는 다른 라이브러리에 직접적으로 전달할 수 있는 파이썬 `SpooledTemporaryFile` 객체를 반환한다.



### `UploadFile`

`UploadFile`은 다음과 같은 어트리뷰트가 있다.

- `filename`: 문자열(`str`)로 된 업로드된 파일의 파일명이다. (예: `myimage.jpg`)
- `content_type`: 문자열(`str`)로 된 파일 형식(MIME type / media type)이다. (예: `image/jpeg`)
- `file`: `SpooledTemporaryFile`(파일류 객체)이다. 이것은 파일류 객체를 필요로하는 다른 라이브러리에 직접적으로 전달할 수 있는 실질적인 파이썬 파일이다.

`UploadFile`에는 다음의 `async` 메소드들이 있다. 이들은 내부적인 `SpooledTemporaryFile`을 사용하여 해당하는 파일 메소드를 호출한다.

- `write(data)`: `data`(`str` 또는 `bytes`)를 파일에 작성한다.
- `read(size)`: 파일으 ㅣ바이트 및 글자의 `size`(`int`)를 읽는다.
- `seek(offset)`: 파일 내 `offset`(`int`) 위치의 바이트로 이동한다.
	- 예) `await myfile.seek(0)` 를 사용하면 파일의 시작부분으로 이동한다.
	- `await myfile.read()` 를 사용한 후 내용을 다시 읽을 때 유용하다.
- `close()`:  파일을 닫는다.

상기 모든 메소드들이 `async` 메소드이기 때문에 "await"을 사용하여야 한다.

예를 들어, `async` 경로 작동 함수의 내부에서 다음과 같은 방식으로 내용을 가져올 수 있다.

```python
contents = await myfile.read()
```

만약 일반적인 `def` 경로 작동 함수의 내부라면, 다음과 같이 `UploadFile.file`에 직접 접근할 수 있다.

```python
contents = myfile.file.read()
```


## 다중 파일 업로드

여러 파일을 동시에 업로드할 수 있다. 그들은 "폼 데이터"를 사용하여 전송된 동일한 "폼 필드"에 연결된다.
이 기능을 사용하기 위해, `bytes`의 `List` 또는 `UploadFile`을 선언해야 한다.

```python
from typing import Annotated
from fastapi import FastAPI, File, UploadFile
from fastapi.responses import HTMLResponse

app = FastAPI()

@app.post("/files/)
async def create_files(files: Annotated[list[bytes], File()]):
	return {"file_sizes": [len(file) for file in files]}
	
@app.post("/uploadfiles/")
async def create_upload_files(files: list[UploadFile]):
	return {"filenames": [file.filename for file in files]}
	
@app.get("/") async def main(): 
	content = """
	 <body> <form action="/files/" enctype="multipart/form-data" method="post"> <input name="files" type="file" multiple> <input type="submit"> </form> <form action="/uploadfiles/" enctype="multipart/form-data" method="post"> <input name="files" type="file" multiple> <input type="submit"> </form> </body> 
	 """
	 return HTMLResponse(content=content)
```

선언한대로, `bytes`의 `list` 또는 `UploadFile`들을 전송받을 것이다.


> 출처: [https://fastapi.tiangolo.com/ko/tutorial/request-files/](https://fastapi.tiangolo.com/ko/tutorial/request-files/)