---
title: JavaScript Quiz2
categories: [TIL, JavaScript]
tags: [JavaScript, Quiz] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 5주차(주특기 입문 - React)

오늘은 새로운 조가 배정되었다!<br>
인사를 마치기 무섭게 새로 지급된 리액트 강의를 듣기 시작했다...<br>
리액트를 해본 적이 없어 두렵기만 한데 금요일까지 제출해야 되는 개인 과제도 생기고..<br>
이번주는 무지 바쁠 것 같다ㅠ

# JavaScript 객관식 문제

**문제 16.** 다음 코드에서 **전개 구문(Spread Syntax)과 관련된 내용**을 고르세요.

```js
const numbers = [1, 2, 3];
const moreNumbers = [4, 5, 6];

const combinedNumbers = [...numbers, ...moreNumbers];

console.log(combinedNumbers);
```

1. `numbers 배열과 moreNumbers 배열의 모든 요소를 병합하여 새로운 배열 combinedNumbers를 생성합니다.`<br>
2. numbers 배열과 moreNumbers 배열의 첫 번째 요소를 병합하여 새로운 배열 combinedNumbers를 생성합니다.<br>
3. numbers 배열과 moreNumbers 배열을 병합하여 numbers 변수에 할당합니다.<br>
4. numbers 배열과 moreNumbers 배열을 순서대로 출력합니다.<br>
   <br>
   <br>

**문제 17.** 다음 코드에서 **나머지 매개변수(Rest Parameter)와 관련된 내용**을 고르세요.

```js
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}

const result = sum(1, 2, 3, 4, 5);

console.log(result);
```

1. `sum 함수는 임의 개수의 인수를 받아서 모두 더한 값을 반환합니다.`<br>
2. sum 함수는 첫 번째 인수와 나머지 인수들을 더한 값을 반환합니다.<br>
3. sum 함수는 나머지 인수들을 배열로 받아서 모두 더한 값을 반환합니다.<br>
4. sum 함수는 첫 번째 인수를 제외한 나머지 인수들을 모두 더한 값을 반환합니다.<br>
   <br>
   <br>

**문제 18.** 다음 코드에서 **템플릿 리터럴(Template Literal)과 관련된 내용**을 고르세요.

```js
const name = "John";
const age = 30;

const message = `My name is ${name} and I am ${age} years old.`;

console.log(message);
```

1. `message 변수에 템플릿 리터럴을 사용하여 문자열을 할당합니다.`<br>
2. `name과 age 변수의 값을 문자열에 삽입하기 위해 템플릿 리터럴을 사용합니다.`<br>
3. name과 age 변수를 이용하여 문자열을 연결하기 위해 템플릿 리터럴을 사용합니다.<br>
4. name과 age 변수의 값을 연산하여 message 변수에 할당합니다.<br>
   <br>
   <br>

**문제 19.** 다음 코드에서 **자료구조 Map과 Set과 관련된 내용**을 고르세요.

```js
const myMap = new Map();

myMap.set("key1", "value1");
myMap.set("key2", "value2");
myMap.set("key3", "value3");

const mySet = new Set();

mySet.add("value1");
mySet.add("value2");
mySet.add("value3");

console.log(myMap.size);
console.log(mySet.size);
```

1. `myMap은 키와 값의 쌍을 저장하는 자료구조로, set 메서드를 사용하여 값을 저장합니다.`<br>
2. `mySet은 중복을 허용하지 않는 값들의 집합을 저장하는 자료구조로, add 메서드를 사용하여 값을 저장합니다.`<br>
3. `myMap.size는 myMap에 저장된 키-값 쌍의 개수를 반환합니다.`<br>
4. `mySet.size는 mySet에 저장된 값의 개수를 반환합니다.`<br>
   <br>
   <br>

**문제 20.** 다음 중 **bind 메서드와 call 메서드의 차이점**은 무엇인가요?<br>

1. bind 메서드는 함수를 호출하지 않고 새로운 함수를 생성하며, call 메서드는 함수를 호출합니다.<br>
2. bind 메서드는 함수에 인자를 전달할 수 있지만, call 메서드는 인자를 전달할 수 없습니다.<br>
3. bind 메서드는 함수를 즉시 실행하고, call 메서드는 함수를 나중에 실행합니다.<br>
4. `bind 메서드는 함수의 컨텍스트를 변경하고, call 메서드는 함수의 인자를 변경합니다.`<br>
   <br>
   <br>

**문제 21.** 다음 **코드의 결과**는 무엇일까요?

```js
const obj = {
  name: "John",
  greeting: function () {
    console.log(`Hello, ${this.name}!`);
  }
};

const obj2 = {
  name: "Alice"
};

obj.greeting.bind(obj2)();
```

1. "Hello, John!"이 출력됩니다.<br>
2. `"Hello, Alice!"가 출력됩니다.`<br>
3. "Hello, undefined!"가 출력됩니다.<br>
4. 에러가 발생합니다.<br>
   <br>
   <br>

**문제 22.** 다음 **코드의 실행 결과**는 무엇일까요?

```js
function greet(name, callback) {
  console.log(`Hello, ${name}!`);
  callback();
}

function sayGoodbye() {
  console.log("Goodbye!");
}

greet("John", sayGoodbye);
```

1. `"Hello, John!"이 출력되고, 그 다음에 "Goodbye!"가 출력됩니다.`<br>
2. "Goodbye!"가 출력되고, 그 다음에 "Hello, John!"이 출력됩니다.<br>
3. "Hello, John!"과 "Goodbye!"가 동시에 출력됩니다.<br>
4. 에러가 발생합니다.<br>
   <br>
   <br>

**문제 23.** **콜백지옥(callback hell)이란** 무엇인가요?<br>

1. `콜백 함수의 연속적인 호출로 인해 코드가 복잡해지고 가독성이 떨어지는 상황을 말합니다.`<br>
2. 콜백 함수가 비동기 작업을 처리하는 동안 발생하는 오류를 의미합니다.<br>
3. 콜백 함수가 무한히 재귀적으로 호출되어 스택 오버플로우가 발생하는 상황을 의미합니다.<br>
4. 콜백 함수가 실행되기 전에 다른 함수에 의해 변경되어 원하는 결과를 얻을 수 없는 상황을 말합니다.<br>
   <br>
   <br>

**문제 24.** 다음 **코드의 실행 결과**는 무엇일까요?

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success!");
  }, 2000);
});

promise.then((result) => {
  console.log(result);
});
```

1. `"Success!"가 2초 후에 출력됩니다.`<br>
2. "Success!"가 즉시 출력됩니다.<br>
3. 에러가 발생하여 아무런 결과도 출력되지 않습니다.<br>
4. 코드가 실행되지 않고 종료됩니다.<br>
   <br>
   <br>

**문제 25.** **Promise 객체를 사용하는 주요한 이유**는 무엇인가요?<br>

1. `비동기 작업을 더 효율적이고 간결하게 처리할 수 있습니다.`<br>
2. 동기 작업에 대해서도 예외 처리를 할 수 있게 합니다.<br>
3. 콜백 함수보다 성능이 우수하고 가독성이 높은 코드를 작성할 수 있습니다.<br>
4. 여러 개의 값을 동시에 반환하고 처리할 수 있습니다.<br>
   <br>
   <br>

**문제 26.** Promise 객체의 catch 메서드는 다음과 같은 상황에서 실행될까요?<br>

1. Promise 체인 중간에 발생하는 오류를 처리하기 위해 호출됩니다.<br>
2. Promise가 성공적으로 해결되었을 때 호출됩니다.<br>
3. `Promise가 거부되었을 때 호출됩니다.`<br>
4. Promise가 아직 해결되지 않은 상태일 때 호출됩니다.<br>
   <br>
   <br>

**문제 27.** 자바스크립트 비동기 처리의 내용 중, **async와 await의 역할로 올바른 것**은 무엇인가요?<br>

1. `async는 함수 내에서 비동기적으로 실행되어야 하는 부분을 지정하고, await는 비동기 작업의 결과를 기다리는 역할을 합니다.`<br>
2. async는 함수 내에서 동기적으로 실행되어야 하는 부분을 지정하고, await는 동기 작업의 결과를 기다리는 역할을 합니다.<br>
3. async와 await은 동일한 역할을 수행하며, 사용 방식만 다릅니다.<br>
4. async는 Promise 객체를 반환하고, await는 콜백 함수를 대기하는 역할을 합니다.<br>
   <br>
   <br>

**문제 28.** 다음 **코드의 실행 결과**는 무엇일까요?

```js
function delay(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function getData() {
  await delay(2000);
  return "Data has been fetched!";
}

async function main() {
  console.log("Start");
  const result = await getData();
  console.log(result);
  console.log("End");
}

main();
```

1. `"Start", "Data has been fetched!", "End"가 순서대로 출력됩니다.`<br>
2. `"Start"가 출력되고, 2초 후에 "Data has been fetched!", 그 다음에 "End"가 출력됩니다.`<br>
3. "Data has been fetched!"가 출력되고, 2초 후에 "Start", 그 다음에 "End"가 출력됩니다.<br>
4. 코드가 실행되지 않고 종료됩니다.<br>
   <br>
   <br>

**문제 29.** **실행 컨텍스트는 무엇을 의미**하는가?<br>

1. `코드의 환경 및 순서를 보장하기 위해 실행할 코드에 제공하는 환경 정보들을 모아놓은 객체이다.`<br>
2. 코드의 실행 결과를 저장하는 객체이다.<br>
3. 코드 실행 중 발생하는 예외를 처리하는 객체이다.<br>
4. 실행 중인 함수의 스택 프레임을 나타내는 객체이다.<br>
   <br>
   <br>

**문제 30.** 다음 **코드의 실행 결과**는 무엇일까요?

```js
function outerFunction() {
  var outerVariable = "Hello";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

var closure = outerFunction();
closure();
```

1. `"Hello"가 출력됩니다.`<br>
2. 에러가 발생하여 아무런 결과도 출력되지 않습니다.<br>
3. "undefined"가 출력됩니다.<br>
4. "outerVariable"이 출력됩니다.<br>
