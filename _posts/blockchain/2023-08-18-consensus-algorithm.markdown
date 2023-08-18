---
layout: post
title:  "합의 알고리즘"
date:   2023-08-18 13:10:00 +0900
categories: 
  - Dev
  - blockchain
tag: blockchain
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 합의 알고리즘

**합의 알고리즘(Consencus Algorithm)**이란, 다수의 참여자가 통일된 의사결정을 하기 위해 사용하는 알고리즘을 말한다. 합의 모델, 합의 방식, 합의 메터니즘 또는 합의 프로토콜이라고도 불린다.

블록체인 시스템의 경우 네트워크에 참여하는 모든 참여자가 동일한 데이털르 복사하여 분산 저장하기 때문에 원본가 사본의 구별이 없으며, 통일된 의사 결정을 내릴 수 있는 권위 있는 중앙(Center)이 존재하지 않는다.

다시 말해, 블록체인의 데이터는 중앙화된 서버 대신 전 세계에 흩어져 있는 수많은 노드에 보관되기 때문의 각가의 노드들은 블록에 기록하는 데이터가 위변조 되지 않은 뭔본이라는 것을 상호 간에 합의하는 과정이 필요하다. 만약 블록을 생성하는, 특정 노드가 악의를 품고 조작도니 데이터를 저장하거나 네트워크에 전파한다면 시스템 전체의 신뢰도가 떨어질 것이다. 이런 악의적인 상황이 발생하더라도 네트워크를 올바른 방향으로 이끌고자 하는 다수의 노드들이 상호 검증을 거쳐 올바른 블록 생성을 이끌어내는 프로세스와 알고리즘을 바로 합의(Consencus)라고 한다.

### 작업 증명(PoW, Proof of Work)

![작업 증명](../../assets/img/blockchain/PoW.png){:.centered}

*작업 증명*

작업 증명은 최ㅅ초의 블록체인인 비트코인을 창시한 사토시 나카모토(Satoshi Nakamoto)가 제안한 합의 알고리즘으로, 블록생성 시간 동안 가장 많은 해시파워를 제공한 노드가 블록을 생성할 수 있도록 설계가 되어 있다. 이 기법은 비트코인, 라이트코인(Litecoin) 등 여러 암호화폐 블록체인에서 사용된다.  

블록을 생성하기 위해 논스(Nonce)라는 임의의 값을 맞히는 과정을 마이닝(Mining, 채굴)이라고 부르는데, 블록체인 네트워크에 전송된 암호화된 거래정보를 새로운 블록에 담고, 새로운 블록을 체인에 연결하는 작업을 완료했다는 것을 증명하는 데 사용되는 컴퓨팅 파워라고 이해할 수 있다. 작업 증명에서는 브랜치가 생긴 경우 가장 긴 블록체인이 남을 때까지 서로 경쟁하여 이긴 브랜치가 최종적으로 브랜치로 채택이 되며, 다른 브랜치는 버려진다.  

작업 증명은 현재 [시빌 공격(Sybil Attack)](http://wiki.hash.kr/index.php/%EC%8B%9C%EB%B9%8C%EA%B3%B5%EA%B2%A9)과 같은 블록체인 네트어크에 대한 각종 공격을 막을 수 있다고 증명된 유일한 알고리즘이다.  

그러나 작업 증명에도 단점이 있다. 가령 A, B, C가 동시에 채굴을 시작했고 C가 채굴에 성공했다. 만약 A와 B가 찾는 논스에 90% 근접했다고 하더라도, 지금 찾는 논스의 값을 계속 찾는 것보다는 새로운 블록을 채굴하는 게 더 효율적이다. 따라서 채굴에 성공한 하나의 노드를 제외한 나머지 모든 노드들은 에너지 자원을 낭비할 뿐이다. 이것이 작업 증명의 가장 큰 단점이다.

| | PoW의 특징 |
| :---: | --- |
| 장점 | - 현재 높은 시장 가치를 형성하고 있는 주류 코인들이 채택하고 있다. <br> - 강력한 보안성을 제공한다. <br> - 서비스 남용을 쉽게 방지할 수 있다. |
| 단점 | - 높은 전력 소모를 통해 자원을 낭비한다. <br> - 지속적으로 해시 파워를 유지해야 한다. <br> - 특정 마이닝 세력의 해시 독점으로 인한 생태계 교란 유려가 있다. |

### 지분 증명(PoS, Proof of Stake)

![지분 증명](../../assets/img/blockchain/PoS.png){:.centered}

*지분 증명*

지분 증명 알고리즘은 노드 또는 사용자가 시스템에 충분한 지분을 갖고 있다는 아이디어에서 출발한다. 즉, PoS는 지분을 많이 가지고 있는 노드에게 블록을 생성할 권한을 준다. 작업이 아닌 더 많은 지분(해당 코인)을 가지고 있을수록 그에 비례하여 블록에 기록할 권한이 더 많이 부여된다는 개념이다.

채굴자에게는 마치 이자와 같은 방식으로 코인이 지급되며, 일정 수 이상의 코인을 보관하고 있는 지갑을 블록체인 네트워크에 연결해놓기만 하면 보상을 받을 수 있다. 블록 생성자와 지분 생성자의 이해관계를 일치시킴으로써 블록을 나쁜 의도로 생성할 동기부여를 없애며, 잘못 생성할 경우 페널티를 부여다.

PoW보다 에너지 소모가 적고, 코인을 가진 노드 누구나 네트워크에 허가 없이 참여하기 때문에 분산화가 더 잘 되어 많은 노드가 의사결정 과정에 쉽게 참여할 수 있는 이점이 있다.

오늘날 **이더리움**은 작업 증명 방식에서 지분 증명 방식으로 합의 알고리즘을 변경하려 한다.

|  | PoS의 특징 |
| --- | --- |
| 장점 | - 해시파워가 많이 필요하지 않으므로 경제적이며 친환경적이다. <br> - 블록 생산자의 탈중앙화로 안정성을 확보할 수 있다. <br> - 블록을 생성하기 위해 지분을 담보로 잡아야 하므로 Dumping을 방지할 수 있다. |
| 단점 | - 아직 검증되지 않았기 때문에 보안성이 강한지 확인되지 않았다. <br> - 지분이 많은 고래들이 권력을 독점할 가능성이 존재한다. |

### 위임 지분 증명(DPoS, Delegated Proof of Stake)

![위임 지분 증명](../../assets/img/blockchain/DPoS.png){:.centered}

*위임 지분 증명*

위임 지분 증명은 PoS에서 변형된 것으로, 시스템의 지분을 가진 각 노드가 투표를 통해 트랜잭션의 유효성 검사를 다른 노드에 위임하여 증명하는 개념이다. **이오스(EOS)**에서 사용된다.

> **이오스(EOS)**는 위임지분증명(DPoS)를 사용하는 제 3세대 암호화폐이다.

모든 노드의 자격을 가진 주주들이 블록 생성에 참여하는 대신, 네트워크의 모든 노드의 투표 결과로 선출한 '상위 노드'(스팀에서는 증인, Witness이라 함)에게 권한을 위임해 합의하도록 하는 방식이다. 일정 수의 증인들(스팀은 20명, EOS는 21명)은 모든 권한을 위임받아 블록 생성을 담당한다. 이는 미국 대선의 대의원 제도 같은 간접선거 방식에 비유할 수 있다.

댄 라리머는 DPoS를 사용하는 그라핀(Graphene) 엔진을 토대로 스팀과 비트셰어를 만들고 이에 대한 성능을 증명했다. DPoS는 합의에 참여하는 노드의 수가 한정되어 있기 때문에 매우 빠른 성능과 확장성을 보이고 있지만, 완전히 탈중앙화된 블록체인이 아니라는 비판을 받고 있기도 하다.

|  | DPoS의 특징 |
| --- | --- |
| 장점 | - PoS에 비해 많은 트랜잭션을 빠르게 처리할 수 있다.
- PoW에 비해 비용이 낮다.
- 하드포크의 위험이 낮다.
- 증인들이 투포에 참여할 인센티브가 분명하다. |
| 단점 | - 증인끼리 손쉽게 담함할 위험이 있다.
- 공개된 소수의 증인에 대한 디도스(DDoS) 공격 위험이 있다. |

### 비잔틴 장애 허용(BFT. Byzantine Fault Tolerance)

비잔틴 장애 허용(BFT. Byzantine Fault Tolerance)이란, 장애가 있더라도 전체의 3분의 1을 넘지 않는다면, 시스템이 정상 작동하도록 허용하는 합의 알고리즘이다.

블록체인의 분산원장 체계가 제대로 돌아가기 위해서는 원장을 공유하는 참여자들이 정직하게 행동해야 하며 이를 보장할 방법이 있어야 한다. 만약 악의적인 노드가 존재하여 누군가 속이려 들더라도 모두가 지닌 원장은 모두가 같은 내용을 유지해야 하는 방법 또한 존재해야 하는데, 이런 골칫거리가 비잔틴 장군의 문제이다. 

### 프랙티컬 비잔틴 장애 허용(PBFT. Practical Byzantine Fault Tolerance)

프랙티컬 비잔틴 장애 허용(PBFT. Practical Byzantine Fault Tolerance)은 네오, 질리카, 하이퍼레저, R3, ITC, 텐더민트 등에서 사용하는 합의 알고리즘이다. 이 기술은 여러 노드로 구성된 네트워크에서 악의적 공격을 방어하기 위해 만들어졌다. 

## 합의 알고리즘의 종류와 장단점

위의 합의 알고리즘 이외에도 다양한 합의 알고리즘이 있으며, 각 합의 알고리즘은 그에 맞는 장단점을 가지고 있다.

<table>
  <thead>
    <tr>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">체인 공개 유형</td>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">합의 방식</td>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">설명</td>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">장점</td>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">단점</td>
      <td style="font-size: 18px; text-align: center; font-weight: bold;">사용 코인</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="font-size: 15px;"> 퍼블릭 <br> 비허가형 <br> 공개형</td>
      <td style="font-size: 15px;">작업 증명 PoW</td>
      <td style="font-size: 12px;">각 노드의 연산 능력을 증명하여 블록 생성 높은 컴퓨팅 파워를 가진 노드가 블록을 생성할 확률이 높음 오랫동안 사용되며 안전성이 검증되었지만 단점도 많이 도출</td>
      <td style="font-size: 15px;">오랫동안 검증됨</td>
      <td style="font-size: 15px;">51% Attack 완결성 문제 느린 트랜잭션 에너지 낭비</td>
      <td style="font-size: 15px;">비트코인 <br> 라이트코인</td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">지분 증명 PoS</td>
      <td style="font-size: 12px;">소유 지분 양에 비례하여 블록 생성 권한을 높은 확률로 부여받음 많은 지분을 가진 노드가 블록을 생성할 확률 높음 이론적으로 우수하지만 실제 대규모 환경에서 검증 사례가 부족</td>
      <td style="font-size: 15px;">51% Attack 내성 빠른 트랜잭션 에너지 낭비 적음</td>
      <td style="font-size: 15px;">완결성 문제 <br> 검증 부족</td>
      <td style="font-size: 15px;">퀀텀 <br> 네오 <br> 스트라디</td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">위임 지분 증명 DPoS</td>
      <td style="font-size: 12px;">일부 위임된 Validator끼리 PoS 수행 트랜잭션 속도가 더 빠름 신뢰도는 Validator의 신뢰도에 종속</td>
      <td style="font-size: 15px;">빠른 트랜잭션 <br> 에너지 낭비 적음</td>
      <td style="font-size: 15px;">완전성 문제 <br> 검증 부족 <br> 탈중앙성 부족 <br> 보안 취약</td>
      <td style="font-size: 15px;">스팀 이오스 <br> 아크 라이</td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">경과 시간 증명 PoET</td>
      <td style="font-size: 12px;">경쟁적 연산으로 낭비되는 에너지를 줄이면서 작업 증명과 유사 효과 하이퍼레저 쏘투스 레이크(Sawtooth Lake)에서 제안 인텔 SGX을 기반으로 블록을 생성하는 리더를 랜덤으로 선정</td>
      <td style="font-size: 15px;">검증된 방법의 개선 에너지 낭비 적음</td>
      <td style="font-size: 15px;">특정 HW 종속</td>
      <td style="font-size: 15px;">쏘투스</td>
    </tr>
    <tr>
      <td style="font-size: 15px;">프라이빗 <br> 허가형 <br> 컨소시엄</td>
      <td style="font-size: 15px;">PBTF</td>
      <td style="font-size: 12px;">참가자 1명이 프라이머리(리더)가 되어 모든 참가자에게 요청 송신 그 요청에 대한 결과를 집계한 뒤 다수의 값을 사용해 블록을 확정 각 노드는 브로드캐스트 된 명령을 받게 되면 모든 노드에 회신 각 노드는 명령을 일정 수 이상 수신하면 명령을 실행하고 블록을 등록</td>
      <td style="font-size: 15px;">완결성 문제 해결 빠른 트랜잭션</td>
      <td style="font-size: 15px;">참여자 사전 파악 필요 <br> 참가자 증가 시 성능 하락</td>
      <td style="font-size: 15px;">페브</td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">권한 증명 PoA</td>
      <td style="font-size: 12px;">트랜잭션 및 블록의 Validator라고 승인된 계정에 의해 유효성이 검사 Validator의 권리를 얻으므로 그들이 얻은 지위를 유지하고자 함 자신의 신원에 부정적 평판이 생기길 원치 않도록 노력할 거라 가정</td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">PAXOS</td>
      <td style="font-size: 12px;">트랜잭션 및 블록의 Validator라고 승인된 계정에 의해 유효성이 검사 Validator가 될 수 있는 권리를 얻으므로 그들이 얻은 지위를 유지하고자 함 자신의 신원에 부정적인 평판이 생기길 원치 않도록 노력할 것이라 가정</td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">RAFT</td>
      <td style="font-size: 12px;">리더를 선정한 후 시스템의 모든 변화를 리더를 통해 결정 <br> 신뢰된 네트워크에서만 사용</td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">리더의 조작 가능 <br> BTF 보장하지 않음</td>
      <td style="font-size: 15px;"></td>
    </tr>
    <tr>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;">Sieve</td>
      <td style="font-size: 12px;">IBM에서 고안한 PBFT 확장 알고리즘 실행결과 전송과 집계 결과 전송으로 흐름이 나뉜다.</td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
      <td style="font-size: 15px;"></td>
    </tr>
  </tbody>
</table>