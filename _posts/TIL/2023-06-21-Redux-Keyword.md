---
title: component
categories: [TIL, React]
tags: [
    React,
    Redux,
    Redux Keyword,
    Action,
    Action Creator,
    Reducer,
    Store,
    Dispatch,
    Subscribe
  ] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 5주차(주특기 숙련 - React)

#### **Redux Keyword**

1. 액션 (Action)<br>
   상태에 변화가 필요할 때 발생시킴 (객체 하나로 표현)

```js
{
  type: "TOGGLE_VALUE";
}
```

type을 필수로 그 외의 값들은 개발자 마음대로,,

```js
{
  type : "ADD_TODO",
  data : {
    id : 0,
    text : '리덕스 배우기'
  }
}
```

```js
{
  type : "CHANGE_INPUT",
  text : '리덕스 배우기'
}
```

2. 액션 생성 함수 (Action Creator)<br>
   액션을 만드는 함수<br>
   단순히 파라미터를 받아와서 액션 객체 형태로 만들어준다.<br>
   컴포넌트에서 더욱 쉽게 액션을 발생시키기 위함 (필수 아님)

```js
export function addTodo(data) {
  return {
    type: "ADD_TODO",
    data
  };
}

// 화살표 함수 사용 예시
export const changeInput = (text) => ({
  type: "CHANGE_INPUT",
  text
});
```

3. 리듀서 (Reducer)<br>
   변화를 일으키는 함수<br>
   두가지 파라미터를 받아옴 (현재의 상태와 액션을 참조하여 새로운 상태를 반환)

   ```js
   function reducer(state, action) {
     // 상태 업데이트 로직
     return alteredState;
   }
   ```

   카운터 리듀서 작성 예시

   ```js
   function counter(state, action) {
     switch (action.type) {
       case "INCREASE":
         return state + 1;
       case "DECREASE":
         return state - 1;
       default:
         return state;
     }
   }
   ```

4. 스토어 (Store)
   한 애플리케이션당 하나의 스토어<br>
   현재의 앱 상태와 리듀서, 내장함수 포함

5. 디스패치 (Dispatch)<br>
   스토어의 내장 함수<br>
   액션을 발생 시키는 것

6. 구독 (Subscribe)<br>
   스토어의 내장 함수<br>
   subscribe 함수에 특정 함수를 전달해주면, 액션이 디스패치 되었을 때 마다 전달해준 함수가 호출<br>
   (리액트에서는 connect 함수 또는 useSelector Hook 을 사용)
