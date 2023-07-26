---
title: TypeScript(1)
categories: [TIL, TypeScript]
tags: [TypeScript] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### `TypeScript란,`

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
};
```

```ts
// test.ts
const sum = (a: number, b: number) => {
  return a + b;
};
```

두 코드는 자바스크립트와 타입스크립트로 작성된 숫자의 합을 구하는 함수 코드 이다.<br>

```js
sum("10", "20"); // 1020
```

만일 두개의 함수에서 위 내용으로 호출한다면,<br>
자바스크립트는 위와 동일하게 문자열을 더한 값이 출력되지만,<br>
타입스크립트는 타입을 명시해두기 때문에 의도하지 않은 코드 동작을 아래와 같이 예방할 수 있다.

```ts
const sum = (a: number, b: number) => {
  return a + b;
};
sum("10", "20");
// Error : '"10"' 형식의 인수는 'number' 형식의 매개 변수에 할당될 수 없습니다.
```

#### [실행 속도]

- 코드 작성 시 타입을 미리 결정하기 때문에 런타임 때 작업을 줄여서 실행 속도가 빠르다.

#### [코드 자동 완성과 가이드]

- 타입스크립트는 코드 작성 시 개발 툴의 기능을 최대로 활용할 수 있다.
- Visual Studio Code는 툴의 내부가 타입스크립트로 작성되어 있어 타입스크립트 개발에 최적화 되어 있다.

### tsc

`tsc = TypeScript 컴파일러`

#### tsconfig.json

- `tsc --init` 명령을 실행하면 생성되는 파일
- TypeScript 프로젝트의 설정 파일
- 주로 프로젝트의 컴파일 옵션 및 입력 파일들을 정의하는데 사용

#### compilerOptions - module 옵션

- 타입스크립트 파일을 컴파일한 후 생성되는 자바스크립트 모듈의 형식을 지정
- 모듈을 가져오고 내부내는 방식을 결정하는 옵션

#### compilerOptions - outDir 옵션

- 컴파일된 자바스크립트 파일이 저장될 출력 디렉터리를 지정

#### compilerOptions - sourceMap 옵션

- 컴파일된 자바스크립트 파일에 대한 소스 맵을 생성하는 옵션
- 소스 맵을 사용하면 실행 중에 에러가 발생했을 때 원래 타입스크립트 소스 코드 위치를 확인할 수 있다.
- 코드 디버깅에 매우 큰 도움이 되기에 개발 환경에서 필히 true설정 권장

#### include , exclude 옵션

- tsc가 컴파일을 할 때 포함하거나 제외할 파일이나 디렉터리를 지정하는 옵션
- “include": ["src/**/*"] > src디렉토리 밑의 데이터를 컴파일 하겠다.
- "exclude": ["node_modules", "dist"] > node_modules, dist 디렉토리 밑의 데이터들은 컴파일 대상에서 제외 하겠다.

#### .d.ts

- 자바스크립트 라이브러리도 타입스크립트 코드에서 사용할 수 있게 해주는 파일
- 타입스크립트 타입 정의 파일
- 외부 라이브러리의 타입을 추론할 수 있음
  > 타입 추론이란, `타입이 명시되지 않았을 때 컴파일러가 알아서 해당 타입에 대해 추론을 하는 것`이다.

### 튜플(tuple)

- 서로 다른 타입의 원소를 순서에 맞게 가질 수 있는 특수한 형태의 배열

#### 튜플과 배열의 차이

- 배열은 number[], string[] 처럼 같은 타입의 원소만 가질 수 있음

```
const testScores : number[] = [90, 85, 78, 92, "88"]
```

> 위의 코드처럼 마지막 원소를 string 타입으로 넣으면 에러가 발생함<br>
> 같은 타입의 원소만 취급 가능

- 튜플은 `어떤 타입의 원소를 허용할 것인지 정의만 해주면 됨`
  > 얼마든지 허용된 타입의 데이터들을 저장할 수 있음

```ts
const person: [string, number, boolean] = ["Spartan", 25, false];
const person2: [string, number, boolean] = [25, "Spartan", false]; //오류
```

> 정의된 데이터 타입의 개수와 순서에 맞추어 저장하는 것이 필수

### enum

- 열거형 데이터 타입
- 다양한 상수를 보다 더 이해하기 쉬운 문자열 이름으로 접근하고 사용할 수 있게 하는 타입
- enum 안에 있는 각 요소는 값이 설정되어 있지 않으면 기본적으로 숫자 0으로 시작
- enum 안에 있는 요소에는 `number` 혹은 `string` 타입의 값만을 할당할 수 있음

### readonly

- 타입스크립트에서 등장한 키워드
- 객체의 속성을 불변으로 만드는 데 사용됨
- 클래스의 속성이나 인터페이스의 속성을 변경할 수 없게 만듦

### any 타입

- 타입스크립트에서 모든 타입의 슈퍼 타입
- 어떤 타입의 값이든 저장할 수 있음
- 자바스크립틔 object 타입과 같은 최상위 타입

```ts
let anything: any;
anything = 5; // 최초에는 숫자를 넣었지만
anything = "Hello"; // 문자열도 들어가고
anything = { id: 1, name: "John" }; // JSON도 들어감
```

### `* 타입스크립트는 프로그램의 타입 안정성을 확보하기 위해 사용되기 때문에 any타입은 코드의 안전성과 유지 보수성을 저해할 수 있어 가급적 사용하지 않기를 권장함`

### unknown 타입

- any 타입과 비슷한 역할을 하지만 더 안전한 방식으로 동작
- 모든 타입의 값을 저장할 수 있음
- 그 값을 다른 타입의 변수에 할당하려면 명시적으로 타입을 확인해야 함
- `typeOf`키워드를 이용하여 타입 체크를 미리한 후 unknown 타입의 변수를 string 타입의 변수에 할당할 수 있음

```ts
let unknownValue: unknown = '문자열!';
let stringValue: string;

if (typeOf unknownValue === 'string') {
  stringValue = unknownValue;
  console.log('unknownValue는 문자열입니다.');
} else {
  console.log('unknownValue는 문자열이 아니었습니다.');
}
```

- unknown 타입이 그나마 재할당을 할 때 타입 체크가 되어서 안전함을 보장함
- 하지만, unknown 타입도 결국 재할당이 일어나지 않으면 타입 안전성이 보장이 되지 않음

### union 타입

- 여러 타입 중 하나를 가질 수 있는 변수를 선언할 때 사용
- | 연산자를 사용하여 여러 타입을 결합하여 표현함

```ts
type StringOrNumber = string | number;
// 원한다면 | boolean 이런식으로 타입 추가 가능

function processValue(value: StringOrNumber) {
  if (typeOf value === 'string') {
    // value는 여기서 string 타입으로 간주됨
    console.log('String value:', value);
  } else if (typeOf value === 'number') {
    // value는 여기서 number 타입으로 간주됨
    console.log('Number value:', value);
  }
}

processValue('Hello');
processValue(42);
```
