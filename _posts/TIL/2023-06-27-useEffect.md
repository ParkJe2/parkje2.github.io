---
title: useEffect
categories: [TIL, React]
tags: [React, useEffect] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 6주차(주특기 숙련 - React)

### **useEffect**
리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 실행할 수 있도록 하는 Hook
- useEffect는 component가 mount됐을 때, component가 unmount됐을 때, component가 update됐을 때, 특정 작업을 처리할 수 있다.
- 즉, 클래스형 컴포넌트에서 사용할 수 있었던 생명주기 메소드를 함수형 컴포넌트에서도 사용할 수 있게 된 것이다.

![Desktop View](image/etc/useEffect.png)
_출처 : http://projects.wojteKmaj.pl/react-lifecycle-methods-diagram/_

#### useEffect() 사용법

- 기본 형태 : useEffect(function, deps)
> function : 수행하고자 하는 작업<br>
> deps : 배열 형태이며, 배열 안에서 검사하고자 하는 특정 값 or 빈 배열

```js
import React, { useEffect } from 'react'
```

useEffect 함수 불러오기

```js
useEffect(() => {
  console.log('마운트 될 때만 실행된다.')
}, []);
```

1. Component가 mount됐을 때 (처음 나타났을 때)
- 컴포넌트가 화면에 가장 처음 렌더링 될 때 한 번만 실행하고 싶을 때는 deps 위치에 빈 배열을 넣는다.
```js
useEffect(() => {
  console.log('렌더링 될 때 마다 실행된다.')
});
```
- 만약 배열을 생략한다면 리렌더링 될 때마다 실행된다.
```js
useEffect(() => {
  console.log(name);
  console.log('업데이트 될 때 실행된다.')
}, [name]);
```

2. Component가 update 될 때 (특정 props, state가 바뀔 때)
- 특정값이 업데이트 될 때 실행하고 싶을 때는 deps 위치의 배열 안에 검사하고 싶은 값을 넣어준다.<br>
(의존값이 들어있는 배열 deps 이라고도 한다. dependency를 의미)
- 업데이트 될 때만 실행하는 것이 아니라 마운트 될 때도 실행된다.
> 따라서 업데이트 될 때만 특정 함수를 실행하고 싶다면 아래와 같은 `꼼수`를 사용하면 좋다.

```js
// 코드 생략

const mounted = useRef(false);

useEffect(() => {
  if(!mounted.current) {
    mounted.current = ture;
  } else {
    // ajax
  }
}, [바뀌는 값])
// 코드 생략
```
- 컴포넌트가 마운트 될 때는 if문에서 아무것도 실행하지 않고 mounted 값만 바꿔주고,<br>
else에서 배열 안에 있는 값이 바뀌면, ajax 서버 통신이라던지 원하는 코드를 실행할 수 있다.

```js
useEffect(() => {
  console.log('effect');
  console.log(name);
  return () => {
    console.log('cleanup');
    console.log(name);
  }})
```

3. Component가 unmount 될 때 (사라질 때) & update 되기 직전에
- cleanup 함수 반환 (return 뒤에 나오는 함수이며 useEffect에 대한 뒷정리 함수라고 한다.)
- 언마운트 될 때만 cleanup 함수를 실행하고 싶을 때<br>
: 두 번째 파라미터로 빈 배열을 넣는다.

- 특정 값이 업데이트 되기 직전에 cleanup 함수를 실행하고 싶을 때<br>
: deps 배열 안에 검사하고 싶은 값을 넣어준다.

### **deps에 특정 값 넣기**
deps에 특정 값을 넣게 된다면 컴포넌트가 처음 마운트 될 때, 지정한 값이 바뀔 때, 언마운트 될 때, 값이 바뀌기 직전에 모두 호출된다.

useEffect 안에서 사용하는 상태나 props가 있다면, deps에 넣어주어야 하는 것이 규칙이다.<br>
만약 사용하는 값을 넣어주지 않는다며면, useEffect 안의 함수가 실행될 때 최신 상태, props를 가리키지 않는다.

deps 파라미터를 생략한다면, 컴포넌트가 리렌더링 될 때마다 useEffect 함수가 호출된다.