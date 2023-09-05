---
title: 객체 구조 분해(Object Destructuring)
categories: [TIL, JavaScript]
tags: [JavaScript, Object, Object Destructuring] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### 객체 구조 분해(Object Destructuring)
Destructuring : 무언가를 파괴 또는 축소하는 것을 의미

JavaScript의 구조 분해는 배열이나 객체에 할당된 데이터에서 특정 값 또는 여러 값을 추출하는 방법이다.

객체의 프로퍼티를 가져오는 가장 일반적인 방법은 점 표기법 또는 대괄호 표기법을 사용하여 동일한 프로퍼티 이름을 작성하는 것이다.

```jsx
const person = {
  name: '먼지',
  age: 20
};

// 점 표기법
const name1 = person.name;
const age1 = person.age;

// 대괄호 표기법

const name2 = person['name'];
const age2 = person['age'];
```

구조 분해를 사용하면 아래의 소스처럼 중괄호를 사용하여 변수 선언과 동시에 객체의 프로퍼티를 가져올 수 있다.

```jsx
const person = {
  name: '먼지',
  age: 20
};

// 점 표기법
const {name, age} = person;
```

구조 분해를 사용할 때, 

중괄호를 사용하므로 마치 객체를 생성하는 것처럼 보일 수 있지만, 실제로 객체를 생성하지는 않는다.

#### 객체 구조 분해 할당 응용하기!!

##### 예제1) 새로운 변수 이름 할당

객체 구조 분해를 사용하여 프로퍼티를 사져와야 하는 경우 변수 이름이 프로퍼티의 이름과 동일해야 한다.

만약, 변수 이름을 프로퍼티 이름과 다르게 설정하고 싶은 경우 콜론(:)뒤에 새로운 변수 이름을 할당한다.


아래 예제는 person 객체의 name 프로퍼티의 값을 가져온 뒤 newName 이라는 변수에 할당한다.

```jsx
const person = {
  name: '먼지',
  age: 20
};

const {name: newName} = person;
console.log(newName) // 먼지
```

##### 예제2) 나머지 연산자

객체 구조 분해에서 나머지 연산자(...)를 사용하면,

객체의 나머지 프로퍼티를 나머지 연산자를 사용한 변수에 할당할 수 있다.

아래 예제는 5개의 프로퍼티르를 가지는 객체에서 나머지 연산자를 사용한다.

```jsx
const numObj = {
  A: 10,
  B: 20,
  C: 30,
  D: 40,
  E: 50
};

const {A, B, ...other} = numObj;

console.log(A); // 10
console.log(B); // 20
console.log(other); // {C: 30, D: 40, E: 50}
```

참고로 나머지 연산자는 무조건 마지막 위치에 존재해야 한다.

만약, 아래 예제처럼 중간에 나머지 연산자를 사용한 경우 SyntaxError가 발생한다

```jsx
const numObj = {
  A: 10,
  B: 20,
  C: 30,
  D: 40,
  E: 50
};

// Uncaught SyntaxError: Rest element must be last element
const {FirstProperty, ...other, LastProperty} = numObj;
```

##### 예제3) 기본 값 설정

객체에 존재하지 않는 프로퍼티의 값을 구조 분해로 가져오는 경우 해당 변수에 undefined가 할당된다.

```jsx
const numObj = {
  A: 10,
  B: 20,
  C: 30
};

const {name, address} = numObj;

console.log(name); // undefined
console.log(address); // undefined
```

객체의 프로퍼티가 존재하지 않거나 undefined가 아닌 기본 값을 설정하고 싶은 경우 아래 예제처럼 변수에 기본 값을 할당할 수 있다.

```jsx
const numObj = {
  A: 10,
  B: 20
};

const {A = 100, B = 200, C = 300} = numObj;

console.log(A); // 10
console.log(B); // 20
console.log(C); // 300
```

객체 numObj에 C라는 프로퍼티가 없으므로 변수 C에 undefined가 할당되어야 하지만, 기본 값을 300으로 설정했으므로 기본 값 300이 할당된다.