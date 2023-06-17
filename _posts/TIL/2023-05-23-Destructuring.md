---
title: Destructuring
categories: [TIL, JavaScript]
tags: [JavaScript, Destructuring] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 2주차(프로그래밍 기초)

오늘은 아침부터 컨디션이 매우 좋지 않았다..ㅠ<br>
잠은 깼는데 몸은 축 쳐지고.. 컴퓨터 화면을 보는 눈은 초점이 흐릿했다.<br>

9시, 첫 시작은 TIL강의를 들었다.<br>
안좋은 예, 굳이 쓰지 않아도 될 예, 등등<br>
모두 내 TIL을 보여주는 것 같아 뜨끔했다....

분명 오전에 강의를 들으면서 "아, 저렇게 쓰는거였구나! 나도 오늘부턴 꼭 저렇게 써야지" 했는데..<br>
막상 쓰려니 또 막힌다..ㅠㅠㅠ

당분간은 TIL 쓰는 것 자체를 익숙해지기 위해 규칙(?) 없이 작성하고,<br>
어느 정도 적응이 된다면.. 제대로 작성해보도록 해야겠다. (걍 맘대로 쓴다는 소리 아님?)

### **구조 분해 할당 (Destructuring)**

```js
배열[]이나 객체{}의 속성을 분해해서 그 값을 변수에 담을 수 있게 해주는 문법

// 배열
let [value1, value2] = [1, "new"];
console.log(value1); // 1
console.log(value2); // "new"

let arr = ["value1", "value2", "value3"];
let [a,b,c] = arr;
console.log(a,b,c) // value1 value2 value3

// let [a,b,c] = arr; 은 아래와 동일!
// let a = arr[0];
// let b = arr[1];
// let c = arr[2];

let [a,b,c,d] = arr
console.log(d) // undefined

let [a,b,c,d = 4] = arr
console.log(d) // 4

------------------------------------------

// 객체
let user = {name: "nbc", age: 30};
let {name, age} = user;

// let name = user.name;
// let age = user.age;

console.log(name, age) // nbc 30

// 새로운 이름으로 할당
let {name: newName, age: newAge} = user;
console.log(name, age) // ReferenceError: name is not defined
console.log(newName, newAge) //nbc 30

let {name, age, birthDay} = user;
console.log(birthDay) // undefined

let {name, age, birthDay = "today"} = user;
console.log(birthDay) // today
```

강의가 너---무 어렵다 ㅠㅠ<br>
생각보다 내용도 많아 복습하려면 한세월...<br>
그래도 놓치면.. 따라가기 힘들 것 같아 꾸준히 연습해야 될 것 같다..
