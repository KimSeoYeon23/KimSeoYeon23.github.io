---
layout: post
title:  "오픈 그래프와 트위터 카드"
date:   2023-06-14 11:45:00 +0900
categories: 
  - Dev
  - html
tag: html
comments: true
---

웹페이지가 소셜 미디어(페이스북, 트위터 등)로 공유될 때 우선적으로 활용되는 정보를 지정

Slack -
![Slack](/assets/img/slackApple.png)  

KaKaoTalk -
![Slack](/assets/img/kakaotalkApple.png)

```html
<!-- Open Graph -->
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Apple (KR)" />
<meta property="og:title" content="iPad 10.2" />
<meta property="og:description" content="강력한 A13 Bionic 칩을 탑재한 iPad. 센터 스테이지 기술이 적용된 12MP 울트라 와이드 전면 카메라, True Tone 디스플레이 기술 및 64GB 저장 용량까지 갖췄습니다." />
<meta property="og:image" content="./images/ipad-seo.png" />
<meta property="og:url" content="https://apple.com/kr/ipad-10.2" />

<!-- Twitter Card -->
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="Apple (KR)" />
<meta property="twitter:title" content="iPad 10.2" />
<meta property="twitter:description" content="강력한 A13 Bionic 칩을 탑재한 iPad. 센터 스테이지 기술이 적용된 12MP 울트라 와이드 전면 카메라, True Tone 디스플레이 기술 및 64GB 저장 용량까지 갖췄습니다." />
<meta property="twitter:image" content="./images/ipad-seo.png" />
<meta property="twitter:url" content="https://apple.com/kr/ipad-10.2" />
```

- `og:type`: 페이지의 유형(E.g, `website`, `video.movie`)
- `og:site_name`: 속한 사이트의 이름
- `og:title`: 페이지의 이름(제목)
- `og:description`: 페이지의 간단한 설명
- `og:image`: 페이지의 대표 이미지 주소(URL)
- `og:url`: 페이지 주소(URL)
- [더 많은 오픈 그래프 속성 보기](https://ogp.me/)

---

- `twitter:card`: 페이지(카드)의 유형(E.g. `summary`, `player`)
- `twitter:site`: 속한 사이트의 이름
- `twitter:title`: 페이지의 이름(제목)
- `twitter:description`: 페이지의 간단한 설명
- `twitter:image`: 페이지의 대표 이미지 주소(URL)
- `twitter:url`: 페이지 주소(URL)
- [더 많은 트위터 카드 보기](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started)