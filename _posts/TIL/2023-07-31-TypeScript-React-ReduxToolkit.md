---
title: TypeScript-React에서 ReduxToolkit 사용해보기
categories: [TIL, TypeScript]
tags: [TypeScript, React, Redux, ReduxToolkit, Redux Hook, dispatch, useSeletor] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### store 설정
- state와 dispatch type을 가져온다.
```ts
import { configureStore } from "@reduxjs/toolkit";
import commentSlice from "./commentSlice";

const store = configureStore({
  reducer: {
    commentSlice,
  },
});
export default store;

// state type 가져오기
export type RootState = ReturnType<typeof store.getState>; 
// dispatch type 가져오기
export type AppDispatch = typeof store.dispatch; 
```

### redux hook 설정
- dispatch 함수와 useSelector 실행을 위해 redux hook을 따로 설정해준다.

```ts
import { useDispatch, useSelector } from "react-redux";
import type { TypedUseSelectorHook } from "react-redux";
// store에서 미리 설정해준 state와 dispatch type
import type { RootState, AppDispatch } from "../redux/store"; 

export const useAppDispatch: () => AppDispatch = useDispatch;
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;
```

위의 설정을 마치면 자바스크립트에서 dispatch에서 사용하는 것과 동일하게 사용할 수 있다.
```ts
import { useAppDispatch, useAppSelector } from "../hook/useRedux";
// 별도로 지정한 eventType
import { FormEvent } from "../type"; 
// Slice의 action함수
import { addComments } from "../redux/commentSlice"; 

export const Form = () => {
	const dispatch = useAppDispatch();
    
    const formData = {...}
    
    const onSubmitHandler = async (e: FormEvent, dispatch: any) => {
        e.preventDefault();
        dispatch(addComments(formData));
    };

    return ( ...
}
```