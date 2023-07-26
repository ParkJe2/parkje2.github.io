---
title: React-Router-Dom
categories: [TIL, React]
tags: [React-Router-Dom] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 8주차(주특기 심화 - React)

### React-Router-Dom

`리액트에서의 페이지 이동`

- 실제 페이지 이동이 일어나지 않음
- index.html에서 안에 있는 것들이 자바스크립트로 바뀜
- 새로고침 없이 화면 전환이 이루어지기에 빠르고 부드러움

#### React-Router-Dom 설치 및 세팅

```
yarn add react-router-dom
```

[기본 세팅]

- index.js에서 전체 앱을 BrowserRouter로 감싸기
- BrowserRouter로 감싸면 Router로 페이지 이동이 가능해짐

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```
