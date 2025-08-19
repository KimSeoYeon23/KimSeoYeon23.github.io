---
layout: post
title: "FastAPI 설치"
date: 2025-08-19 10:36:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}


## FastAPI 설치

### 가상 환경인지 확인하기

명령 프롬프트 왼쪽에 (venv) 프롬프트가 보이는지 확인한다. 만약 명령 프롬프트 왼쪽에 (venv) 프롬프트가 보이지 않는다면 가상 환경에 진입한 상태에서  FastAPI 설치를 진행한다.

### 가상 환경에서 FastAPI 설치하기

venv 가상 환경에 진입한 상태에서 pip install fastapi 명령을 입력한다. pip은 파이썬 라이브러리를 설치하고 관리해 주는 파이썬 도구다. `pip install fastapi` 명령은 pip을 이용해 FastAPI를 설치하라는 명령어라고 생각하면 된다. 다음 화면이 나오면 FastAPI가 잘 설치된 것이다.

```bash
(fastapi) kimseoyeon:fastapi/ (main✗) $ uv add fastapi                  [16:19:31]
Resolved 11 packages in 235ms
Prepared 8 packages in 172ms
Installed 10 packages in 27ms
 + annotated-types==0.7.0
 + anyio==4.10.0
 + fastapi==0.116.1
 + idna==3.10
 + pydantic==2.11.7
 + pydantic-core==2.33.2
 + sniffio==1.3.1
 + starlette==0.47.2
 + typing-extensions==4.14.1
 + typing-inspection==0.4.1
```