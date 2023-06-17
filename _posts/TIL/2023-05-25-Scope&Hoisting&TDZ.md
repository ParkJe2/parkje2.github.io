---
title: Scope & Hoisting & TDZ
categories: [TIL, JavaScript]
tags: [Scope, Hoisting, TDZ] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 2주차(프로그래밍 기초)

벌써 자바스크립트 강의 공부를 시작한 지 4일이 됐다!<br>
당장 금요일에 과제 발제가 있을 예정이다 보니 안그래도 짧은 시간이 더욱 짧게 느껴진다.<br>

이해가 안되는 부분이나 어려워서 다시 보고 싶은 부분을 놓고 넘어가질 않으니 진도가 나가지 않고 계속 제자리 걸음이라 우선 쭉 보고 다시 복습을 해야될 것 같다..<br>

## **스코프, 호이스팅, TDZ**

### **스코프 (Scope)**

- 자바스크립트의 스코프는 함수 레벨 스코프를 따른다.
- 같은 함수 레벨에 존재하면 값을 참조할 수 있다는 것으로 ES6에서 let 키워드가 도입되면서 블록 레벨 스코프를 사용할 수 있게 됐다.

```
▷ **전역 스코프** : 어디서든 참조 가능

▷ **전역 변수** : 전역 스코프를 갖는 전역 변수 (어디서든 참조 가능)

▷ **지역 스코프** : 함수 자신과 하위 함수에서만 참조 가능

▷ **지역 변수** : 지역 스코프를 갖는 지역 변수
함수 내에서 선언된 변수로 해당 함수와 해당 함수의 하위 함수에서 참조 가능

▷ **임묵적 전역 변수** : 선언하지 않은 변수에 값을 할당하면 전역 객체의 프로퍼터가 되어 전역 변수처럼 동작한다.
하지만 변수 선언이 없었기 때문에 호이스팅은 발생하지 않는다.
```

```js
(variable = 1) === (window.variable = 1);

//////////////////////////////////////

console.log("test", test);

function temp() {
  test = 10;
}

temp(); // test is not defined
```

### **호이스팅 (Hoisting)**

- 함수의 코드를 실행하기 전에 변수와 함수의 메모리 공간을 선언 전에 미리 할당 하는 것
- 초기화를 제외한 선언만 호이스팅
- 그렇기 때문에 선언, 정의된 코드보다 호출하는 코드를 먼저 배치할 수 있음
- 변수의 선언과 초기화를 분리
- 변수의 선언을 코드의 최상단으로 끌어올림

```js
catName("먼지");

function catName(name) {
  console.log("제 고양이의 이름은 " + name + "입니다");
}

// "제 고양이의 이름은 먼지 입니다"
```

▷ **변수 선언 현식에 따른 초기화**

**var** : 호이스팅 시 undefined로 변수를 초기화

**function** : 선언된 위치와 상관없이 동일하게 호출

**let,const** : 호이스팅 시 변수를 초기화하지 않음 (호이스팅 대상은 맞음)

```js
console.log(num); // 호이스팅한 var 선언으로 인해 undefined 출력
var num; // 선언
num = 6; // 초기화

console.log(num2); // ReferenceError: num2 is not defined
let num2 = 2;

//-----------------------------------------------

catName("휴지"); // "제 고양이의 이름은 휴지 입니다"

function catName(name) {
  console.log("제 고양이의 이름은 " + name + "입니다");
}

catName("휴지"); // "제 고양이의 이름은 휴지 입니다"
```

### **TDZ (Temporal Dead Zone, 일시적 사각지대)**

- TDZ의 영향을 받는 구문 const, let, class
- 변수 스코프의 맨 위에서부터 ~ 변수의 초기화 완료 시점까지의 변수는 TDZ에 들어간 변수
- 코드의 작성 순서(위치)가 아니라 코드의 실행 순서(시간)에 의해 형성

▷ **let, const**

```js
{
  // <----- TDZ가 스코프 맨 위에서부터 시작
  const func = () => console.log(letVar); // OK

  // TDZ 안에서 letVar에 접근하면 ReferenceError

  let letVar = 3; // letVar의 TDZ 종료 ------->

  func(); // TDZ 밖에서 호출함
}
```

let 변수 선언 코드가 그 변수에 접근하는 함수보다 아래에 위치하지만 함수의 호출 시점이 사각지대 밖이므로 정상 동작

▷ **class**

부모 클래스를 상속받을 경우, 생성자 안에서 super()호출을 하기 전까지 this바인딩은 TDZ안에 있다.

```js
// (X)
class User extends Member {
  constructor(phone) {
    this.phone = phone;
    super(phone);
  }
}

// (O)
class User extends Member {
  constructor(phone) {
    super(phone);
    this.phone = phone;
  }
}
```

※ TDZ는 선언 전에 변수를 사용하는 것을 허용하지 않는다.
※ var의 사용은 의도치 않은 중복 선언과 재할당으로 문제가 생길 수 있기 때문에 사용하지 않는 편이 좋다.
