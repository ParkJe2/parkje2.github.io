---
title: TypeScript-React에서 ReduxToolkit 사용해보기
categories: [TIL, TypeScript]
tags: [TypeScript, React, Redux, ReduxToolkit, Redux Hook, dispatch, useSeletor] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### Styled-components 설치
```
yarn add styled-components
```

### 타입스크립트 - 타입 정의 받기
```
yarn add @types/styled-components
```

### 글로벌스타일 적용하기
- createGlobalStyled으로 전역 스타일 설정

```ts
import { createGlobalStyle } from 'styled-components';

export const GlobalStyle = createGlobalStyle`
  /* 글로벌 스타일 작성하기  */
`;

// 최상위 컴포넌트 : App.js 또는 index.js 등등 원하는 최상위에 코드 추가 
import {GlobalStyle} from '파일경로/global-style.ts'

const App = () => (
  <>
    <GlobalStyle /> 
    <div>최상위 컴포넌트</div>
  </>
);
```

### 스타일 작성하기
- props를 styled-component에 넘겨줄 때 타입을 지정하지 않으면 오류가 난다.

```ts
//text.ts
<Text done={done}>{text}</Text>
//testStyle.ts
// 오류 코드
export const Text = styled.div`
  flex: 1;
  font-size: 21px;
  color: #495057;
  ${({ done }) =>
    done &&
    css`
      color: #ced4da;
    `}
`;

// 정상 코드
export const Text = styled.div<{ done: boolean }>`
  flex: 1;
  font-size: 21px;
  color: #495057;
  ${({ done }) =>
    done &&
    css`
      color: #ced4da;
    `}
`;
```

- 단일 props 사용 시

```ts
const Container = styled.div< { age : number } >`
  color: ${(props) => (props.age > 20 ? 'red' : 'gray')};
`;
```

- 다수 props 사용시 : interface 작성

```ts
// Container styled-components에 적용할 interfacer를 작성
interface Container extends 상속타입 {
  isActive: boolean;
  age: number;
  프롭스명: 타입지정;
}
// styled-components에 interface 타입 지정하기
const Container = styled.div<Container>`
  color: ${(props) => (props.age > 20 ? 'red' : 'gray')};
  background-color: ${(props) => (props.isActive ? 'red' : 'gray')};
`;
```

- 상속 컴포넌트에 타입지정

```ts
// 상속컴포넌트의 타입 상속받기
interface Container {
  isActive: boolean;
  age: number;
  프롭스명: 타입지정;
}

// 상속받은 컴포넌트에 타입 추가하기
const Container = styled(상속받을 컴포넌트명)<Container>`
  color: ${(props) => (props.age > 20 ? 'red' : 'gray')};
  background-color: ${(props) => (props.isActive ? 'red' : 'gray')};
`;
```