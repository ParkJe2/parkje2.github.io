---
title: Redux TooKit
categories: [TIL, React]
tags: [Redux TooKit] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 7주차(주특기 심화 - React)

### **Redux TooKit**

Redux-Toolkit은 Redux를 만든 곳에서 공식적으로 효율적인 Redux 개발을 위해 만들어진 툴킷이다.

Redux 작성하는 코드를 간단하게 작성할 수 있고, Redux 보다 훨씬 효율적이므로 사용을 공식적으로 강력히 권장하한다.

Redux의 3가지 문제점

- Redux 스토어 구성이 너무 복잡하다.
- Redux에서 유용한 작업을 수행하려면 많은 패키지를 추가해야 한다.
- Redux에는 너무 많은 상용구 코드가 필요하다.
위 문제점을 Redux-Toolkit을 사용하면 해결할 수 있다.

Redux를 사용하기 위해 Redux-Toolkit을 사용해야 하는 것은 아니지만, 모든 Redux앱엔 Redux-Toolkit을 사용하는 것이 좋다고 말한다.

새로운 Redux 사용자이든 기존 애플리케이션을 단순화하려는 숙련된 사용자이든 Redux-Toolkit을 사용하면 코드가 더 개선되고 유지 관리가 쉬워 진다고 말한다.

### **Redux-Toolkit이 제공하는 것**

**`configureStore`**
: 간단하게 Store를 만들 수 있도록 도와준다.

**`createReducer`**
: switch문을 작성하는 것 대신 간단하게 Reducer를 만들 수 있도록 도와준다.

**`createAction`**
: Reducer에 작성한 것들을 기반으로 Action들을 만들어 준다.

**`createSlice`**
: reducer의 이름, 초기상태, reducers 등을 간편하게 만들 수 있도록 도와준다.

**`createAsyncThunk`**
: createAction을 비동기로 만들 수 있도록 도와준다.

**`createSelector`**
: Store에서 상태를 효율적으로 저장하도록 도와준다.