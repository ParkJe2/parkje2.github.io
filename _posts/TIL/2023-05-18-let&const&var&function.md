---
title: let & const & var & function
categories: [TIL, JavaScript]
tags: [let, const, var, function] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 1주차(Mini Project)

1주차 마지막 날!<br>

오늘은 팀프로젝트 마지막 날!<br>
마무리 작업 후 오후 시간에 조별 발표를 진행했다.<br>
발표자도 아닌데 순서가 다가오니 두근두근,,<br>
우리 조 발표자는 영빈님이다! 분명 발표 하는 거 안좋아 하신다고 하셧던 것 같은데..<br>
연습할 때도 잘 하셨지만 실전 타입이신가... 너무 잘해서 놀랐다!!<br>
만약 내가 발표자였다면......ㅎ 설명은 무슨.. 국어책 읽다가 끝났을 것 같다.<br>

프로젝트 과정 중 충돌 문제도 발생했었지만 나름 일찍 해결이 되서 마지막 날은 개인 공부 시간을 나름 많이 가졌다.<br>
다음주부턴 조가 새로 바뀔 텐데 너무 아쉽다 ㅠㅠ

## let, const, var, function 의 실행 원리

### **let**

let 명령문은 블록 스코프의 범위를 가지는 지역 변수를 선언하며, **선언과 동시에 임의의 값으로 초기화**할 수도 있다.

```js
let var1 [= value1] [, var2 [= value2]] [, ..., varN [= valueN]];
```

### **const**

const 선언은 블록 범위의 상수를 선언한다.<br>
**상수의 값은 재할당 할 수 없으며, 다시 선언할 수도 없다.**

```js
const name1 = value1 [, name2 = value2 [, ... [, nameN = valueN]]];
```

### **var**

var 문은 변수를 선언하고 **선택적으로 초기화 할 수 있다.**

```js
var varname1 [= value1 [, varname2 [, varname3 ... [, varnameN]]]];
```

### **function**

Function 생성자는 새 Function 객체를 만든다.<br>
이 생성자를 직접 호출하여 동적으로 함수를 생성할 수도 있으나, 보안 문제 및 eval (en-US)과 유사한(그러나 훨씬 덜 심각한) 성능 문제가 발생할 수 있다.<br>
하지만 eval과 달리, Function 생성자는 전역 범위로 한정된 함수만 생성한다.

모든 JavaScript 함수는 사실 Function 객체다.<br>
이는 "(function(){}).constructor === Function"이 참을 반환하는 것에서 알 수 있다.

```js
new Function ([arg1[, arg2[, ...argN]],] functionBody)
```

- **변수 중복 선언 불가**

[let]

**let** 키워드로는 **변수 중복 선언이 불가**하지만, **재할당은 가능**하다.

```js
let name = "Tom";
console.log(name); // output: Tom

let name = "jeri"; // output: Uncaught SyntaxError: Identifier 'name' has already been declared

name = "munji";
console.log(name); // output: munji
```

[const]

**const**가 let과 다른 점이 있다면, 반드시 **선언과 초기화를 동시에 진행**되어야 한다.

```js
const name; // output: Uncaught SyntaxError: Missing initializer in const declaration
const name = 'TOM'
```

const도 let과 마찬가지로 재선언이 불가하며, 더 나아가 재할당도 불가하다.<br>
재할당의 경우, 원시 값은 불가능하지만, 객체는 가능하다.<br>
const 키워드는 **재할당을 금지할 뿐, ‘불변’을 의미하지 않는다.**

```js
// 원시값의 재할당
const name = "munji";
name = "huji"; // output: Uncaught TypeError: Assignment to constant variable.

// 객체의 재할당
const name = {
  eng: "munji"
};
name.eng = "huji";

console.log(name); // output: { eng: "howdy" }
```

- 블록 레벨 스코프

let, const 키워드로 선언한 변수는 모두 코드 블록(ex. 함수, if, for, while, try/catch 문 등)을 지역 스코프로 인정하는 블록 레벨 스코프를 따른다.

위 var 키워드로 예를 들었던 것을 그대로 가져와 바꾸면 아래와 같은 결과가 나온다.

```js
let a = 1;

if (true) {
  let a = 5;
}

console.log(a); // output: 1
```

var 키워드로 선언한 경우 5가 나왔지만, let 키워드로 선언한 경우 if 문 안에 있는 것은 지역 스코프를 가져 전역에서 console을 찍었을 경우,<br>
전역에 있는 a가 결과 값으로 출력된다. (const 키워드도 let 키워드와 동일하게 동작한다)

- 변수 호이스팅

[let]

let 키워드로 선언한 변수는 선언 단계와 초기화 단계가 분리되어 진행된다.<br>
즉, 런타임 이전에 자바스크립트 엔진에 의해 선언 단계가 먼저 실행되지만, 초기화 단계가 실행되지 않았을 때 해당 변수에 접근하려고 하면 참조 에러가 뜬다.

```js
console.log(name); // output: Uncaught ReferenceError: name is not defined

let name = "huji";
```

따라서 let 키워드로 선언한 변수는 스코프의 시작 지점부터 초기화 단계 시작 지점까지 변수를 참조할 수 없는 일시적 사각지대(Temporal Dead Zone: TDZ) 구간에 존재한다.

[const]

const 키워드는 선언 단계와 초기화 단계가 동시에 진행된다.

```js
console.log(name); // output: Uncaught ReferenceError: Cannot access 'name' before initialization

const name = "jeri";
```

let 키워드로 선언한 경우, 런타임 이전에 선언이 되어 자바스크립트 엔진에 이미 존재하지만 초기화가 되지 않았기 때문에 name is not defined라는 문구가 떴다.<br>
하지만 const 키워드로 선언한 경우, 선언과 초기화가 동시에 이루어져야 하지만 런타임 이전에는 실행될 수 없다.<br>
따라서 초기화가 진행되지 않은 상태이기 때문에 Cannot access 'name' before initialization 에러 문구가 뜬다.

※ 기본적으로 변수의 스코프는 최대한 좁게 만드는 것을 권장한다.<br>
따라서, var 키워드 보다는 let과 const 키워드를 사용하며, 변경하지 않는 값(상수)이라면 let 보다는 const 키워드를 사용하는 것이 안전하다.
