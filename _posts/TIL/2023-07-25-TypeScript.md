---
title: TypeScript
categories: [TIL, TypeScript]
tags: [TypeScript] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### ⁉️`Typrscript`
- JavaScript에 타입을 부여한 언어
- JavaScript의 확장된 언어 (자바스크립트의 단점은 줄이고 더 좋은 기능을 감싼 형태)
- ES5의 상위확장 이므로 기존의 자바스크립트(ES5) 문법을 그대로 사용할 수 있고,<br>
ES6의 새로운 기능들을 사용하기 위해 Babel과 같은 별도 트랜스파일러를 사용하지 않아도 ES6의 새로운 기능을 기존의 자바스크립트 엔진에서 실행할 수 있다.
- JavaScript와 호환되는 것은 물론 클래스, 인터페이스 등 객체지향 프로그래밍 패턴을 제공한다.

### TypeScript 설치 방법
- Visual Studio Code
- Node.js
- npm

#### 설치 명령어 (MAC)
```
npm i -g typescript
```

### TypeScript의 장점
- 에러 사전 방지
- 실행 속도
- 개발 생산성 향상 (코드 가이드 및 자동 완성)
- 안전성
- 협업용이성

#### [에러 사전 방지]
- 타입스크립트는 에러를 사전에 미리 예방할 수 있다.
> 예시코드
```js
// test.js
const sum = (a, b) => {
  return a + b;
}
```
```ts
// test.ts
const sum = (a: number, b: number) => {
  return a + b;
}
```
두 코드는 자바스크립트와 타입스크립트로 작성된 숫자의 합을 구하는 함수 코드 이다.<br>
```js
sum('10', '20'); // 1020
```
만일 두개의 함수에서 위 내용으로 호출한다면,<br>
자바스크립트는 위와 동일하게 문자열을 더한 값이 출력되지만,<br>
타입스크립트는 타입을 명시해두기 때문에 의도하지 않은 코드 동작을 아래와 같이 예방할 수 있다.
```ts
const sum = (a: number, b: number) => {
  return a + b;
}
sum('10', '20'); // Error : '"10"' 형식의 인수는 'number' 형식의 매개 변수에 할당될 수 없습니다.
```

#### [실행 속도]
- 코드 작성 시 타입을 미리 결정하기 때문에 런타임 때 작업을 줄여서 실행 속도가 빠르다.

#### [코드 자동 완성과 가이드]
- 타입스크립트는 코드 작성 시 개발 툴의 기능을 최대로 활용할 수 있다.
- Visual Studio Code는 툴의 내부가 타입스크립트로 작성되어 있어 타입스크립트 개발에 최적화 되어 있다.
