---
layout: post
title:  "compression"
date:   2025-12-24 09:50:00 +0900
categories: 
  - Dev
  - node
tag: node
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

> 많은 양의 데이터가 네트워크 전송 시 네트워크에 부담을 줄 수 있는데, compression은 서버에서 데이터를 압축 하여 준다. 이를 통해 서버는 클라이언트로 데이터를 전송할 때, 압축된 데이터를 보냄으로써 네트워크 전송 속도를 높이고, 비용을 줄일 수 있다.

  

## 사용법

```Bash
npm i compression --save
```

  

### compression을 이용하여 데이터 압축하기 전

![](https://i.imgur.com/qs25Vis.png)


compression을 사용하기 이전에 관리자 도구 > 네트워크 탭에서 데이터의 정보를 확인해보면, 데이터의 크기는 128kb이고, 시간은 274ms가 걸렸다.

  

### compression을 사용한 경우

```JavaScript
import express from 'exress';
import compression from 'compression';

const app = express();

app.use(compression(());
```

![](https://i.imgur.com/Hbsy8tw.png)


![](https://i.imgur.com/ffvOxTv.png)


compression을 사용한 경우 데이터의 크기는 38.6kb로 줄어들었고, 시간 또한 220ms로 줄어든 것을 확인할 수 있다.

  

![](https://i.imgur.com/uNT3ldA.png)


또 한 가지 특이한 것은, `Content-Encoding`이 gzip으로 되어 있는 것을 확인 할 수 있다.

  

- **gzip**
    
    GUNzip이라고도 불리는 Gzip은 파일 압축에 쓰이는 응용 소프트웨어이다. 이 Gzip을 쓰는 이유에 대해 알기 위해서는 우선 일반적인 트랜잭션이 일어났을 때의 상황을 가정하고 그림로 나타낸 것을 먼저 볼 것이다.
    
    ![](https://i.imgur.com/MjXC2Fi.png)

    
    위와 같은 상황이라고 했을 때, 클라이언트가 `hi.html`을 서버로 요청했고, 서버가 이 요청을 읽었다. 이후 서버가 응답을 보내줬고, 이 응답을 띄우는데 이 응답이 500kb짜리인 상황이다. 500kb의 데이터가 전송되는 상황에 반해, Gzip을 사용한 경우를 예시로 들어볼 것이다.
    
    Gzip은 이 서버가 보내주는 응답을 압축해 버리는 것이다.
    
    ![](https://i.imgur.com/IiMzchH.png)

    
    위 사진과 같이 압축해서 보내버리면 응답 자체가 압축되기에, 네트워크 비용을 크게 절감할 수 있게 된다. 일반적으로 이 Gzip을 사용하면 평균적으로 70% 정도 크기가 줄어들게 된다.
    
      
    

## 옵션

- **level**
    - 압축 정도를 설정하는 것으로 **-1**에서 **9**까지 가능하다. **1**이 기본 압축을 의미하며, **-1**은 압축을 하지 않은 것이며, nodejs 환경에서는 **6**으로 설정하는 것이 가장 최적화 하는 수준이다.
- **threshold**
    - 압축하지 않는 최소한의 크기를 설정하는 것이다. 예를 들어 `threshold: 100 * 1000`은 100kb 아래의 데이터는 압축하지 않고, 클라이언트에게 전송한다.
- **filter**
    - 특정 조건에 따라 압축을 할 지 말지 결정하는 것이다.

  

### 예시 코드

```JavaScript
import express from 'exress';
import compression from 'compression';

const app = express();

app.use(compression({
	level: 6,
	threshold: 100 * 1000,
	filter: (req, res) => {
		if (req.headers["x-no-compression"]) {
			// header에 x-no-compression이 있으면, 압축하지 않도록 false를 반환한다.
			return false
		}
		return compression.filter(req, res);
		// 없는 경우에는 압축 허용
	}
}))
```


  

> 출처: [https://mihee0703.tistory.com/109](https://mihee0703.tistory.com/109)