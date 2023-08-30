---
layout: post
title:  "이더리움 클라이언트(Ethereum Client)"
date:   2023-08-30 23:10:00 +0900
categories: 
  - Dev
  - blockchain
tag: blockchain
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

이더리움 클라이언트(Ethereum Client)는 이더리움 블록체인 네트워크를 구성하는 개별 클라이언트 노드(Node)이기 때문에 중앙집중형 서버 프로그램이 따로 존재하지 않으며, 오로지 클라이언트 프로그램만 존재하게 된다. 이더리움 클라이언트는 멀티 플랫폼 환경을 지원하기 위해 다양한 프로그램이 언어로 개발되고 있다.

## Geth

Geth는 이더리움 재단(Ethereum Foundation)이 제공하는 공식 클라이언트 소프트웨어로써, Go언어로 개발되었다.  
Geth를 처음 시작하면 네트워크 내의 다른 이더리움 클라이언트(노드; Node라고도 불림)에 연결하는 작업을 먼저 시작하고 블록체인의 전체 사본을 내려받게 된다. 그리고 블록체인의 복사본을 최신 상태로 유지하기 위해 끊임없이 다른 노드와 통신한다.  
또한 Geth를 이용해 블록을 채굴하고, 블록체인에 트랜잭션을 추가하고 블록의 트랜잭션을 검증하며 트랜잭션을 실행할 수도 있으며, RPC를 통해 상호작용할 수 있는 API를 노출하여 서버 역할을 하기도 한다.

> 블록체인에 연결할 수 있는 자바스크립트 클라이언트(Geth Console)도 있다.

![Geth Console을 사용한 이더리움 블록체인 네트워크](../../assets/img/blockchain/geth_console.png){:.cetnered}
*Geth Console을 사용한 이더리움 블록체인 네트워크*

## Parity

패리티(Parity)는 이더리움 프로토콜의 또 다른 구현체이며, 러스트(Rust) 프로그래밍 언어로 개발되었다. 현재 Parity Inc.라는 기업에서 운영되고 있다.  
사실 이더리움 네트워크에 접속할 수 있는 클라이언트 소프트웨어를 개발하는 길은 누구에게나 열려 있으며, C++, 파이썬 및 다른 언어로 작성된 클라이언트도 있다. 우리가 원한다면 [이더리움 황서](http://paper.gavwood.com/)를 참고하여 자신의 클라이언트를 구현할 수도 있다.

![Parity Browser를 사용한 이더리움 블록체인 네트워크](../../assets/img/blockchain/parity.png){:.centered}
*Parity Browser를 사용한 이더리움 블록체인 네트워크*

## 비트코인과 이더리움의 또 다른 차이점

| **구분** | **비트코인** | **이더리움** |
| :---: | :---: | :---: |
| 암호화폐 | 1세대 | 2세대 |
| 기능 | 비트코인의 거래기록만 블록체인에 적용 | 계약을 기록할 수 있는 스마트 컨트랙트 기술 추가 |
| 채굴 방식 | PoW | PoS |
| 상한 채굴 개수 | 약 2,100만 개 까지 | 상한 없이 생산 |