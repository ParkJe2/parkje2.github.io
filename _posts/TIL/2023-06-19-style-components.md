---
title: component
categories: [TIL, CSS, React]
tags: [React, CSS, style component] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 5주차(주특기 숙련 - React)

#### **Styled Components**

- CSS-in-JS 라이브러리 중에 가장 널리 사용되고 있는 라이브러리

## 패키지 설치

```js
$ npm i styled-components
```

설치 후, `package.json`에 `styled-components`가 추가된 것을 확인할 수 있다.

```js
{
  "name": "styled-components",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.14.1",
    "@testing-library/react": "^13.0.0",
    "@testing-library/user-event": "^13.2.1",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "styled-components": "^6.0.0-rc.3",
    "web-vitals": "^2.1.0"
  }
```

## **기본 문법**

- 컴포넌트를 임포트 후 인자로 해당 컴포넌트를 넘긴다.

```js
import styled from "styled-components";
import Button from "./Button";

styled(Button)`
  // <Button> React 컴포넌트에 스타일 정의
`;
```

- ES6의 Tagged Template Literals을 사용해서 스타일을 정의하며,
  styled 함수는 결국 해당 스타일이 적용된 React 컴포넌트를 리턴한다.

예를 들어, 다음과 같이 Styled Components로 작성된 JavaScript 코드는

```js
import styled from "styled-components";

styled.button`
  font-size: 1rem;
`;
```

아래 CSS 코드가 적용된 엘리먼트를 만들어낸다고 생각하면 쉽다.

```js
button {
  font-size: 1rem;
}
```

이런 식으로 Styled Components를 이용해서 JavaScript 코드 안에 삽입된 CSS 코드는 글로벌 네임 스페이스를 사용하지 않는다.<br>
다시 말해, 각 JavaScript 파일마다 고유한 CSS 네임 스페이스를 부여해주기 때문에, 각 React 컴포넌트에 완전히 격리된 스타일을 적용할 수 있게 된다.

이것은 순수하게 CSS만을 사용했을 때는 누리기 어려웠던 대표적인 CSS in JS의 장점 중 하나 이다.
