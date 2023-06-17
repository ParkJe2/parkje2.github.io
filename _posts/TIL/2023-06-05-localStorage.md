---
title: localStorage
categories: [TIL, JavaScript]
tags: [localStorage] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 4주차(프로그래밍 기초)

## **localStorage**

- 브라우저의 key-value 값을 Storage에 저장할 수 있음
- 세션이 바뀌어도 저장한 데이터가 유지됨
- Storage 타입은 웹 브라우저에서 데이터를 저장하고 관리하는 메소드를 제공
- localStorage 객체는 Storage 타입으로 비휘발적으로 데이터를 저장할 수 있게 함
- localStorage는 문자열만 저장할 수 있음
- 객체를 저장하려면 JSON.stringify() 메소드로 문자열로 변환한 다음 저장해야 함.
  반대로 저장된 문자열 값을 가져와서 다시 객체로 변환하려면 JSON.parse() 메소드를 사용

### **Storage 타입**

- setItem() : key, value 추가
- getItem() : value 읽어오기
- removeItem() : item 삭제
- claer() : 도메인 내의 localStorage 값 삭제
- length : 전체 item 갯수
- key() : index로 key값 찾기

### **localStorage 접근**

- window 객체의 속성을 통해 localStorage에 접근할 수 있음

```js
window.localStorage;
```

- localStorage가 Storage 타입의 객체이기 때문에 storage의 메소드를 호출하여 데이터를 관리할 수 있음

### **localStorage에 아이템 추가, 읽기**

**setItem()**
localstorage에 아이템을 추가(저장)하기 위해서는 setItem() 함수를 사용

```js
window.localStorage.setItem(key, value);
```

**getItem()**
localStorage의 아이템을 읽기 위해서는 getItem() 함수를 사용

```js
window.localStorage.getItem(key);
```

```js
// setItem()
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", "1");
/* localStorage에 key-value를 저장
localStorage에는 문자열만 저장 가능
숫자를 저장하더라도 문자열만 저장됨 */

// getItem()
const name = window.localStorage.getItem("name");
const age = window.localStorage.getItem("age");
/* getItem() 함수에 key를 전달하여 localStorage에 저장된 값을 읽어왔다.
 */

// 출력
console.log(name); // munji
console.log(age); // 1
```

### **localStorage에 객체, 배열 저장하기**

```js
// localStorage에 저장할 객체
const obj = {
  name : 'munji',
  age : 1
}

// localStorage에 저장할 배열
const arr = [1, 2, 3];

// 객체, 배열을 JSON 문자열로 변환
const objString = JSON.stringify(obj);
const arrString - JSON.stringify(arr);
/* localStorage에는 문자열만 저장되기에 객체, 배열을 저장하기 위해 문자열로 변환해서 저장 필요!!
JSON.stringify() 함수를 사용하여 객체와 배열을 JSON 문자열로 변환함 */

// setItem
window.localStorage.setItem('person', objString);
window.localStorage.setItem('num', arrString);
/* JSON 문자열을 localstorage에 저장 */

// getItem
const personString = window.localStorage.getItem('person');
const numString = window.localStorage.getItem('num');

// JSON 문자열을 객체, 배열로 변환
const personObj = JSON.parse(personString);
const numArr = JSON.parse(numString);

// 출력
console.log(personString) // {'name':'munji', 'age':1}
console.log(personObj); // [object Object]
console.log(numsString); // [1,2,3]
console.log(numsArr); // 1,2,3
```

### **localStorage에 값 삭제하기**

**removeItem()**

```js
window.localStorage.removeItem(key);
```

```js
// setItem
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", "1");

// removeItem
window.localStorage.removeItem("name");
// removeItem() 함수를 사용하여 key가 'name'인 아이템 삭제
window.localStorage.removeItem("Gender");
/* 'Gender'라는 key는 localStorage에 존재하지 않음
removeItem에 존재하지 않는 key를 파라미터로 전달할 경우 아무 일도 일어나지 않음!! */

// getItem
const name = window.localStorage.getItem("name");
const age = window.localStorage.getItem("age");

// 출력
console.log(name); // null
console.log(age); // 20
```

### **localStorage에 값 전체 삭제하기**

**clear()**

```js
window.localStorage.clear();
```

```js
// setItem
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", "1");

// clear
window.localStorage.clear();
// localStorage 도메인의 모든 아이템을 삭제

// getItem
const name = window.localStorage.getItem("name");
const age = window.localStorage.getItem("age");

// 출력
console.log(name); // null
console.log(age); // null
```

### **localStorage의 아이템 갯수 구하기**

**length**

```js
window.localStorage.longth;
```

```js
// 초기화
window.localStorage.clear();

// setItem
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", 1);

// localStorage item 갯수
const length = window.localStorage.length;
// localStorage에 저장된 값의 갯수를 확인하기 위해 length 속성 사용

// 출력
console.log(length); // 2
```

### **localStorage의 key 이름 찾기**

**key()**

```js
window.localStorage.key(index);
```

```js
// setItem
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", "1");

// key
const key_1 = window.localStorage.key(0);
const key_2 = window.localStorage.key(1);
// key() 함수의 파라미터로 index를 전달하여 해당 index의 key 값을 조회

// 출력
console.log(key_1); // age
console.log(key_2); // name
```

### **전체 key, value 가져오기**

## **for문**

```js
// 초기화
window.localStorage.clear();

// setItem
window.localStorage.setItem("name", "munji");
window.localStorage.setItem("age", 1);

// 모든 key, value 출력
// output => age : 1 / name : munji
for (i = 0; i < window.localStorage.length; i++) {
  // length 속성을 사용하여 전체 아이템의 길이를 구하여 for문 실행

  // key 찾기
  const key = window.localStorage.key(i);
  // for문의 index 값과 key() 함수를 사용하여 key 이름을 읽어옴

  // value 찾기
  const value = window.localStorage.getItem(key);
  // 앞에 찾아온 key값과 getItem() 함수를 이용하여 해당 key의 value를 읽어옴

  // 출력
  console.log(key + ":" + value + "<br />");
}
```

### **for...in**

- for...in 문에서는 사용자가 정의한 key 이외에 localStorage의 built-in 항목까지 조회되기에 built-in 항목을 제거해줘야 함

```js
// 초기화
window.localStorage.clear();

// setItem
window.localStorage.setItem("name", "munji");
widnow.localStorage.setItem("age", 1);

// output => age : 1 / name : munji
for (const key in widnow.localStorage) {
  if (window.localStorage.hasOwnProperty(key)) {
    // for...in 문에서 조회되는 built-in 항목을 제거하기 위해 hasOwnProperty() 함수 사용

    // value 찾기
    const value = window.localStorage.getItem(key);

    // 출력
    console.log(key + ":" + value + "<br />");
  }
}
```

### **Object.keys()**

```js
// 초기화
window.localStorage.clear();

// setItem
window.localStorage.setItem("name", "munji");
widnow.localStorage.setItem("age", 1);

// key 목록 조회 / 출력
const keys = Object.keys(window.localStorage);
// localStorage의 key 목록을 조회하기 위해 Object.keys() 함수 사용
console.log(keys);
console.log("<br/>");

// 모든 key, value 출력
// output => age,name / age : 20 / name : munji
for (const key of keys) {
  // value 찾기
  const value = window.localStorage.getItem(key);

  // 출력
  console.log(key + ":" + value + "<br />");
}
```
