---
title: async & await
categories: [TIL, JavaScript]
tags: [async, await] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 3주차(프로그래밍 기초)

## **async / await**

- ES2017에 도입된 문법, Promise 로직을 더 쉽고 간결하게 사용할 수 있게 해줌
- 단, Promise를 대체하기 위한 기능이 아니며 내부적으로는 여전히 Promise를 사용하여 비동기 처리를 하되, 프로그래머가 유지보수하기 편하게 보이는 문법만 다르게 해줄 뿐이다.

### **async / await 기본 사용법**

- function 키워드 앞에 async 를 붙이고, 비동기 처리되는 부분 앞에 await만 붙여주면 된다.

```js
async function test() {
  // logic
}

변수 = async () => {
  // logic
};
```

### **async / await 사용 예제**

```js
function asyncTest() {
  return new Promise((resolve, reject) => {
    const test = [1, 2, 3];
    resolve(test);
  });
}

async function logTest() {
  const result = await asyncTest();
  console.log(result);
}
```

asyncTest 함수는 Promise()객체를 반환하는 함수이다.<br>
resolve() 함수를 사용했기 때문에 test 배열을 반환해야 한다.<br>
만약 await를 사용하지 않고 promise(), then()을 사용했을 경우 코드가 길어져 가독성이 떨어졌을 것이다.

### **async / await 예외 처리**

async / await에서 예외를 처리하는 방법은 try ~ catch이다.<br>
promise에서 예외 처리를 위해 .catch()를 이용했던 것처럼 async에서는 catch {} 를 이용하면 된다.

```js
async function test() {
  try {
    const user = await fetchUser();
    if (user.id === 1) {
      const todo = await fetchTodo();
      console.log(todo.title);
    }
  } catch (err) {
    console.log(error);
  }
}
```
