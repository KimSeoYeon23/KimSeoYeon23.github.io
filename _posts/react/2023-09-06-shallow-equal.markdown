---
layout: post
title:  "useCallback"
date:   2023-09-06 22:10:00 +0900
categories: 
  - Dev
  - react
tag: react
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## useCallback을 이용한 함수 최적화

원래 컴포넌트가 렌더링 될 때 그 안에 있는 함수도 다시 만들게 된다. 하지만 똑같은 함수를 컴포넌트가 리 렌더링된다고 해서 **계속 다시 만드는 것**은 좋은 현상은 아니다. 그리고 이렇게 컴포넌트가 리 렌더링 될 때마다 함수를 계속 다시 만든다고 하면 만약 이 함수가 자식 컴포넌트에 `props`로 내려 준다면 함수를 포함하고 있는 컴포넌트가 리 렌더링 될 때마다 **자식 컴포넌트도 함수가 새롭게 만들어지니 계속 리 렌더링** 하게 된다.

![useCallback 1](../../assets/img/react/usecallback_1.png){:.centered}

### 리렌더링 테스트

**함수 생성하기**

```js
const B = ({ message, posts }) => {
  console.log('B Component is Rendering');
  const testFunction = () => {};
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
*console.log로 어떤 컴포넌트가 렌더링 되는지 확인*

**props로 함수 넘겨주기**
```js
const List = React.memo(({ posts, testFunction }) => {
  console.log('List Component is Rendering');
  return (
    <ul>
      {posts.map((post) => {
        return <ListItem key={post.id} post={post} />;
      })}
    </ul>
  );
});

const B = ({ message, posts }) => {
  console.log('B Component is Rendering');
  const testFunction = () => {};
  return (
    <div>
      <h1>B Component</h1>
      <Message message={message} />
      <List posts={posts} testFunction={testFunction} />
    </div>
  );
};
```

### Input에 입력

텍스트 입력으로 어떤 컴포넌트가 렌더링 되는지 확인한다.

![텍스트](../../assets/img/react/test_text.JPG) | ![console.log](../../assets/img/react/console.JPG)

원래 React.memo로 감싸줘서 리 렌더링이 되지 않던 컴포넌트들이 한 글자 입력 시마다 `List` 컴포넌트까지 다시 리 렌더링 되는 걸 볼 수 있다.

### React.useCallback 적용으로 문제 해결

`useCallback`은 **메모이제이션 된 함수**를 반환하는 함수이다.

`useCallback` 적용은 `useCallback` 안에 콜백함수와 의존성 배열을 순서대로 넣어주면 된다.

```js
const testFunction = useCallback(() => {}, []);
```

함수 내에서 참조하는 `state, props`가 있다면 의존성 배열에 추가하면 된다.  

`useCallback`으로 인해서 의존성 배열에 추가된 `state` 혹은 `props`가 변하지 않는다면 함수는 새로 생성되지 않는다.  
새로 생성되지 않기 때문에 메모리에 새로 할당되지 않고 동일 참조 값을 사용하게 된다.  

의존성 배열에 아무것도 없다면 컴포넌트가 최초 렌더링 시에만 함수가 생성되며 그 이후에는 동일한 참조 값을 사용하는 함수가 된다.

### 적용 후 다시 타이핑 시

![console.log](../../assets/img/react/console_2.JPG){:.centered}

이제는 렌더링이 필요치 않은 `List` 컴포넌트가 없는 것을 볼 수 있다.


## useCallback을 사용하기 좋은 때

`useCallback`도 모든 함수에 다 사용하기 보다는 사용하는 자체로서 비용이 들기 때문에 정말 필요할 때에 사용하는 게 좋다.

1. 자식 컴포넌트가 `React.memo()`로 최적화 되어 있고
2. 그 자식 컴포넌트에게 해당 함수를 `props`로 넘겨줄 때
  
`useCallback`을 사용하는 것이 유용하다.