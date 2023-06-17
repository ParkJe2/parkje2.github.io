---
title: URL parameter
categories: [TIL, JavaScript]
tags: [URL parameter] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 4주차(프로그래밍 기초)

## **URL parameter 가져오기**

- location.href를 이용하여 현재 페이지 전체 URL을 가져올 수 있음
- localtion.search를 이용하여 현재 페이지 URL의 Parameter를 가져올 수 있음

## 전체 값 가져오기

```js
const searchParams = new URLSearchParams(location.search);

for (const param of searchParams) {
  console.log(param);
}
```

- new URLSearchParams 함수를 사용하면 location.search 안에 존재하는 [key, value] 형식으로 묶여있는 파라미터를 얻을 수 있게됨
