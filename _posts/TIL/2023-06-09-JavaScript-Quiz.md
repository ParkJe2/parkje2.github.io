---
title: JavaScript Quiz
categories: [TIL, JavaScript]
tags: [JavaScript, Quiz] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 4주차(프로그래밍 기초)

오늘은 팀 프로젝트 제출일이다.<br>
오전에 마지막 머지를 끝내고 개인 공부를 진행했다.

자바스크립트 강의 복습을 하려던 와중에 객관식 문제(30개)를 공유해주셔서 오늘은 그 중 15문제를 풀어봤다..!

# JavaScript 객관식 문제

**문제 1.** **자바스크립트의 동적 타이핑**이란 무엇을 의미하는가요?<br>

1. 모든 변수 타입이 동일하다는 것<br>
2. `변수의 타입이 런타임 시점에 결정된다는 것`<br>
3. 변수의 타입이 프로그램이 실행되는 동안에 변경될 수 없다는 것<br>
4. 변수를 선언할 때 반드시 타입을 지정해야 한다는 것<br>
   <br>
   <br>

**문제 2.** 자바스크립트에서 **var로 선언된 변수는 어떻게 작동**하나요?<br>

1. 같은 이름의 변수를 여러 번 선언하면 오류가 발생한다.<br>
2. 선언 후에 값을 변경할 수 없다.<br>
3. `같은 이름의 변수를 여러 번 선언해도 오류가 발생하지 않고, 가장 마지막에 선언한 값으로 변수가 덮어씌어진다.`<br>
4. var로 선언된 변수는 메모리에 저장되지 않는다.<br>
   <br>
   <br>

**문제 3.** 자바스크립트에서 **const로 선언된 변수에 대한 설명 중 틀린 것**은 무엇인가요?<br>

1. const는 선언 후에 값을 변경할 수 없는 상수를 선언할 때 사용된다.<br>
2. 같은 이름의 변수를 두 번 선언하면 오류가 발생한다.<br>
3. `const로 선언된 변수는 값을 변경할 수 있다.`<br>
4. const는 ES6에서 새로 도입된 변수 선언 방법이다.<br>
   <br>
   <br>

**문제 4.** **"Hello" / 2의 결과값**은 무엇인가요?<br>

1. 2<br>
2. "Hello2"<br>
3. `NaN`<br>
4. undefined<br>
   <br>
   <br>

**문제 5.** 자바스크립트에서 find() 메서드가 주어진 함수를 만족하는 배열의 첫 번째 요소를 반환하는 다음 예제를 참고하세요.

```js
let array = [5, 12, 8, 130, 44];
let found = array.find((element) => element > 10);
```

이 코드에서 **found 변수의 값**은 어떻게 될까요?<br>

1. 5<br>
2. `12`<br>
3. 8<br>
4. 130<br>
   <br>
   <br>

**문제 6.** 다음 **코드의 출력 결과**는 무엇일까요?

```js
function add(x, y) {
  return x + y;
}

console.log(add(2, 3));
```

1. 2<br>
2. 3<br>
3. `5`<br>
4. undefined<br>
   <br>
   <br>

**문제 7.** **주어진 배열의 모든 요소를 제곱하여 새로운 배열을 생성하는 코드**는 다음 중 어떤 것인가요?<br>

1. `transformedArray = array.map(num => num \* num);`<br>
2. transformedArray = array.filter(num => num \* num);<br>
3. transformedArray = array.reduce((acc, num) => acc + num \* num, []);<br>
4. transformedArray = array.slice().map(num => num \* num);<br>
   <br>
   <br>

**문제 8.** 다음 **코드의 출력 결과**는 무엇일까요?

```js
let square = (x) => x * x;

console.log(square(3));
```

1. 3<br>
2. 6<br>
3. `9`<br>
4. undefined<br>
   <br>
   <br>

**문제 9.** **do...while문이 하는 일**은 무엇인가요?<br>

1. 초기값, 조건식, 증감식을 사용하여 반복 횟수를 제어한다.<br>
2. `일단 한 번은 코드를 실행하고, 그 후에 조건식을 체크하여 반복 여부를 결정한다.`<br>
3. 조건식이 참인 경우에만 코드를 반복해서 실행한다.<br>
4. 객체의 프로퍼티를 순서대로 접근한다.<br>
   <br>
   <br>

**문제 10.** 아래 **코드의 출력 결과**는 무엇인가요?

```js
let count = 0;
while (count < 5) {
  console.log(count);
  count++;
  if (count === 3) {
    break;
  }
}
```

1. 0<br>
2. 0 1<br>
3. 1 2<br>
4. `0 1 2`<br>
   <br>
   <br>

**문제 11.** 아래 **코드의 출력 결과**는 무엇인가요?

```js
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

const entries = Object.entries(person);

console.log(entries);
```

1. `["name", "John"], ["age", 30], ["city", "New York"]`<br>
2. `["name: John", "age: 30", "city: New York"]`<br>
3. `["John", 30, "New York"]`<br>
4. `오류 발생`<br>
   <br>
   <br>

**문제 12.** 다음 코드에서 **함수와 관련된 내용**을 고르세요.

```js
const numbers = [1, 2, 3, 4, 5];

const doubledNumbers = numbers.map((num) => num * 2);

console.log(doubledNumbers);
```

1. `numbers 배열의 각 요소를 2배로 만들어서 새로운 배열 doubledNumbers를 생성합니다.`<br>
2. numbers 배열에서 짝수인 요소만 필터링하여 새로운 배열 doubledNumbers를 생성합니다.<br>
3. numbers 배열에서 인덱스 1부터 4까지의 요소를 추출하여 새로운 배열 doubledNumbers를 생성합니다.<br>
4. numbers 배열을 그대로 복사하여 새로운 배열 doubledNumbers를 생성합니다.<br>
   <br>
   <br>

**문제 13.** 다음 코드에서 **삼항 연산자와 관련된 내용**을 고르세요.

```js
const num = 10;

const result = num > 5 ? "Greater than 5" : "Less than or equal to 5";

console.log(result);
```

1. `num 변수가 5보다 크다면 'Greater than 5' 문자열을, 그렇지 않다면 'Less than or equal to 5' 문자열을 result 변수에 할당합니다.`<br>
2. num 변수가 5보다 작다면 'Greater than 5' 문자열을, 그렇지 않다면 'Less than or equal to 5' 문자열을 result 변수에 할당합니다.<br>
3. num 변수가 5보다 크다면 true를, 그렇지 않다면 false를 result 변수에 할당합니다.<br>
4. num 변수가 5보다 작다면 true를, 그렇지 않다면 false를 result 변수에 할당합니다.<br>
   <br>
   <br>

**문제 14.** 다음 코드에서 **구조 분해 할당(Destructuring Assignment)과 관련된 내용**을 고르세요.

```js
const person = {
  name: "John",
  age: 30,
  country: "USA"
};

const { name, age, country } = person;

console.log(name, age, country);
```

1. `person 객체의 name, age, country 속성을 각각 변수 name, age, country에 할당합니다.`<br>
2. person 객체의 name, age, country 속성을 배열로 할당하고, 순서대로 변수 name, age, country에 할당합니다.<br>
3. person 객체의 속성 중에서 name, age, country만을 선택하여 새로운 객체를 생성합니다.<br>
4. person 객체의 속성 중에서 name, age, country만을 선택하여 새로운 배열을 생성합니다.<br>
   <br>
   <br>

**문제 15.** 다음 코드에서 **단축 속성명(Shorthand Property Name)과 관련된 내용**을 고르세요.

```js
const name = "John";
const age = 30;

const person = {
  name,
  age,
  country: "USA"
};

console.log(person);
```

1. `name과 age 변수의 값을 각각 person 객체의 name과 age 속성으로 할당합니다.`<br>
2. person 객체의 name과 age 속성을 각각 name과 age 변수의 값으로 초기화합니다.<br>
3. person 객체의 name과 age 속성을 name: name, age: age와 같이 명시적으로 할당합니다.<br>
4. person 객체의 속성 중에서 name과 age 속성만을 선택하여 새로운 객체를 생성합니다.<br>
   <br>
   <br>
