---
title: Redux-toolkit
categories: [TIL, React]
tags: [React, Redux, Redux-toolkit] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 8주차(주특기 심화 - React)

### Redux-toolkit 설치 및 기본세팅
설치 명령어
```
yarn add react-redux @reduxjs/toolkit
```

기본 세팅
- configureStore로 데이터 중앙 저장소 만들기
```jsx
import { configureStore } from "@reduxjs/toolkit";

const store = configureStore({
  reducer: {},
});
```
- 어플리케이션 최상위에 Provider 두기
```jsx
import { Provider } from "react-redux";

root.render(
    <Provider store={store}>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </Provider>
);
```
- 최종 코드
```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import "./index.css";
import { BrowserRouter } from "react-router-dom";
// 1. 리덕스에 필요한 코드 import
import { configureStore } from "@reduxjs/toolkit";
import { Provider } from "react-redux";

// 2. configureStore 사용하기
const store = configureStore({
  reducer: {},
});

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
		{/* 3. Provider로 전체 앱 감싸고 store에 위에 configureStore 넣어주기 */}
    <Provider store={store}>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </Provider>
  </React.StrictMode>
);
```
