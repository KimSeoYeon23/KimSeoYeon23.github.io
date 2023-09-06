---
layout: post
title:  "리액트 앱 성능 테스트"
date:   2023-09-06 20:20:00 +0900
categories: 
  - Dev
  - react
tag: react
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## 리액트 앱 성능 측정하기

![화면](../../assets/img/react/react_performance_test.png){:.centered}

### 앱 구현하기

성능을 측정하기 위한 앱을 먼저 구현한다.  

1. 리액트 설치  
  `npx create-react-app react-performance-app`

2. 전체 구조 생성  
  A와 B포넌트를 같은 기능이지만 다르게 만들어서 `Profiler`로 성능을 비교해 본다.  
  A: 컴포넌트 하나에 구현  
  B: 여러 컴포넌트로 구현

3. 가짜 데이터 가져오기  
  성능을 측정하기 위해서는 어느 정도 많은 데이터가 있을 시에 측정이 가능하기 때문에 가짜 데이터를 전달해주는 곳에 요청을 보내서 가짜 데이터를 받아오겠다.

   ```js
     useEffect(() => {
       fetch('https://jsonplaceholder.typicode.com/posts')
         .then((res) => res.json())
         .then((posts) => setPosts(posts));
     }, []);
   ```


- **App.js**
  - 데이터 가져오기
  - 검색창
  - 전체적인 레이아웃

```js
import { useEffect, useState } from 'react';
import './App.css';
import A from './components/A';
import B from './components/B';

function App() {
  const [value, setValue] = useState('');
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((res) => res.json())
      .then((posts) => setPosts(posts));
  }, []);

  return (
    <div style={{ padding: '1rem' }}>
      <input value={value} onChange={(e) => setValue(e.target.value)} />
      <div style={{ display: 'flex' }}>
        <A message={value} posts={posts} />
        <B message={value} posts={posts} />
      </div>
    </div>
  );
}

export default App;
```
*App.js*

- **A.js**
  - 모든 요소를 하나의 컴포넌트에 넣는다.

```js
import React from 'react';

const A = ({ message, posts }) => {
  return (
    <div>
      <h1>A Component</h1>
      <p>{message}</p>
      <ul>
        {posts.map((post) => {
          return (
            <li key={post.id}>
              <p>{post.title}</p>
            </li>
          );
        })}
      </ul>
    </div>
  );
};

export default A;
```
*A.js*

- **B.js**
  - 여러 컴포넌트로 나눠준다.

```js
import React from 'react';

const Message = ({ message }) => {
  return <p>{message}</p>;
};

const ListItem = ({ post }) => {
  return (
    <li key={post.id}>
      <p>{post.title}</p>
    </li>
  );
};

const List = ({ posts }) => {
  return (
    <ul>
      {posts.map((post) => {
        return <ListItem key={post.id} post={post} />;
      })}
    </ul>
  );
};

const B = ({ message, posts }) => {
  return (
    <div>
      <h1>B Component</h1>
      <Message message={message} />
      <List posts={posts} />
    </div>
  );
};

export default B;
```
*B.js*

### React Profiler로 앱 성능 측정하기

성능을 측정하기 위해 크롬 개발자 도구를 열고 `Profiler` 탭으로 이동한다.

![React Profiler](../../assets/img/react/react_profiler.png){:.centered}

해당 탭에서 프로파일링을 수행해서 성능 데이터를 기록하고 측정할 수 있다.  

프로 파일링을 수행하려면 레코드 버튼을 클릭한다.

Profiler는 컴포넌트가 재 렌더링이 될 때마다 성능을 기록한다.

![React Profiler Test](../../assets/img/react/react_profiler_test.png){:.centered}

![Profiler "h"](../../assets/img/react/profiler_h.JPG){:.centered}

1. **1번째 "h"를 타이핑해서 Re Rendering 했을 때**
   1. App Component: 5.7ms
   2. A Component: 2.2ms
   3. B Component: 3.4ms
   4. A Component Rendering Time < B Component Rendering Time

결과, 컴포넌트를 여러 개로 쪼갠 B Component가 속도가 더 느리게 나왔다.

### React.memo를 이용한 성능 최적화

현재 앱에서 B 컴포넌트는 `B`, `List`, `ListItem`, `Message` 컴ㅍ노넌트로 나눠져 있다. 이렇게 나눠준 이유는 재사용성을 위해서도 있지만 각 컴포넌트의 렌더링의 최적화를 위해서 이기도 하다. 예를 들어서 `Input`에서 글을 타이핑을 할 때 원래는 `Message` 컴포넌트와 그 `State` 값을 가지고 있는 `App` 컴포넌트만 렌더링이 돼야 하는데 현재는 상관이 없는 다른 부분까지 렌더링 되고 있다.

- `React.memo` 적용으로 문제 해결
  - `React.memo` 적용은 간단하게 원하는 컴포넌트를 `React.memo`로 감싸주면 된다.
  
  ```js
  const Message = React.memo(({ message }) => {
    return <p>{message}</p>;
  });

  const ListItem = React.memo(({ post }) => {
    return (
      <li key={post.id}>
        <p>{post.title}</p>
      </li>
    );
  });

  const List = React.memo(({ posts }) => {
    return (
      <ul>
        {posts.map((post) => {
          return <ListItem key={post.id} post={post} />;
        })}
      </ul>
    );
  });
  ```


![렌더링 테스트](../../assets/img/react/hello_rendering.gif){:.centered}

이제는 렌더링이 필요치 않은 `List`, `ListItem` 컴포넌트는 렌더링이 안 되는 걸 볼 수 있다.

![렌더링 속도](../../assets/img/react/rendering_time.JPG){:.centered}

B 컴포넌트의 렌더링 속도가 엄청나게 향상한 것을 볼 수가 있다.

## React.memo() 란?

React는 먼저 컴포넌트를 렌더링(rendering) 한 뒤, 이전에 렌더링 된 결과와 비교하여 DOM 업데이트를 결정한다. 만약 렌더링 결과가 이전과 다르다면, React는 DOM을 업데이트한다.  

이 과정에서 만약 컴포넌트가 `React.memo()`로 둘러 쌓여 있다면, React는 컴포넌트를 렌더링하고 결과를 메모이징(Memoizing)한다. 그리고 다음 렌더링이 일어날 때 렌더링하는 컴포넌트의 props가 같다면, React는 메모이징(Memoizing)된 내용을 재사용한다.

> 메모이제이션(Memoization) 이란?  
> Memoization은 주어진 입력 값에 대한 결과를 저장함으로써 같은 입력값에 대해 함수가 한 번만 실행 되는 것을 보장한다.


### React Memo Props 비교 방식 수정하기

비교 방식을 원하는 대로 수정하고 싶다면 React.memo()의 두 번째 매개변수로 비교 함수를 넣어주면 된다.

```js
React.memo(Component, [compareFunction(prevProps, nextProps)]);
```

```js
function compareFunction(prevProps, nextProps) {
  return (
    prevProps.a === nextProps.a && prevProps.b === nextProps.b
  )
}
```
*`true`일 경우 메모제이션 된 것을 사용, `false`일 경우 새로운 것을 사용*
*a, b, c, d가 `props`로 있을 때 a가 이전과 같고 b가 이전과 같으면 `true => true`이면 c, d는 달라졌으도 a, b가 같으면 메모이제이션 된 컴포넌트를 사용해 준다.*

### React Memo 사용을 지양해야 하는 상황

렌더링 될 때 `props`가 다른 경우가 대부분인 컴포넌트를 생각해보면, 메모이제이션 기법의 이점을 얻기 힘들다.  
`props`가 자주 변하는 컴포넌트를 `React.memo()`로 래핑 할지라도, React는 두 가지 작업을 리 렌더링 할 때마다 수행한다.

1. 이전 `props`와 다음 `props`의 동등 비교를 위해 비교 함수를 수행한다.
2. 비교 함수는 거의 항상 `false`를 반환할 것이기 때문에, React는 이전 렌더링 내용과 다음 렌더링 내용을 비교한다.

비교 함수의 결과는 대부분 `false`를 반환하기 때문에 `props` 비교는 불필요하게 된다.

### React.memo()는 리 렌더링을 막기 위한 도구보다 성능 개선의 도구 (official site에서 추천)

React에서는 성능 개선을 위한 하나의 도구로 메모이제이션을 사용한다.  

대부분의 상황에서 React는 메모이징 된 컴포넌트의 리 렌더링을 피할 수 있지만, 렌더링을 막기 위해 메모이제이션에 너무 의존하면 안된다. (버그 유발 가능성이 있다.)