---
title: 얕은 복사(shallow copy)와 깊은 복사(deep copy)
categories: [TIL, JavaScript]
tags: [JavaScript, shallow copy, deep copy] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 2주차(프로그래밍 기초)

아침에 일어나는게 점점 익숙해져야 하는데<br>
이상하게 갈수록 더 힘들다..<br>
처음보다 나름 일찍자는데 (4시 -> 1~2시)<br>

무튼,,<br>
오늘은 오전에 git 2차 강의를 들었다.<br>
터미널 쓰는 건 저어어엉말 익숙해지지 않는다 ㅠㅠ<br>
써버릇(?) 해야되는데 계속 vs코드 연결해서 쉬운 방법만 찾고 있다;;<br>
근데 더 큰 문제는.. 자바스크립트 공부하다 갑자기 깃 강의듣고 다시 자바스크립트 강의 듣고 사실 집중이 잘 안된다 ㅠㅠ<br>
오늘은 특히나 더 어려웠다..!

### **얕은 복사(shallow copy)와 깊은 복사(deep copy)**

▷ **얕은 복사 (shallow copy)**

얕은 복사란,<br>
**'주소 값'을 복사**한다는 의미이다.
(주소 값을 복사하기에 참조하고 있는 실제 값은 같음)

```js
const obj1 = { a: 1, b: 2 };
const obj2 = obj1;

console.log(obj1 === obj2); // true
```

위의 예시처럼 객체를 직접 대입하는 경우 참조에 의한 할당이 이루어지므로 둘은 같은 데이터(주소)를 가지고 있다.

```js
const obj1 = { a: 1, b: 2 };
const obj2 = obj1;

obj2.a = 100;

console.log(obj1.a); // 100
```

위 두 객체는 같은 데이터(주소)를 가지고 있고, 그래서 같은 주소를 참조하고 있다.<br>
때문에 obj2의 property를 수정하고, obj1를 출력해도 obj2 값과 동일하다.

```js
* 얕은 복사 방법

[Array.prototype.slice()]
```

얕은 복사 방법의 대표적인 예라고 할 수 있다.<br>
**start부터 end 인덱스까지 기존 배열에서 추출하여 새로운 배열을 리턴하는 메소드** 이다.<br>
만약 start와 end를 설정하지 않는다면, 기존 배열을 전체 얕은 복사한다.

```js
const original = ["a", 2, true, 4, "hi"];
const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

copy.push(10);

console.log(JSON.stringify(original) === JSON.stringify(copy)); // false

console.log(original); // [ 'a', 2, true, 4, 'hi' ]
console.log(copy); // [ 'a', 2, true, 4, 'hi', 10 ]
```

기존 배열에는 영향을 끼치지 않아서 깊은 복사로 보일 수 있지만, 원시값을 저장한 1차원 배열일 뿐이다.<br>
원시값은 기본적으로 깊은 복사다. **Slice() 메소드는 기본적으로 얕은 복사를 수행**한다.

```js
const original = [
  [1, 1, 1, 1],
  [0, 0, 0, 0],
  [2, 2, 2, 2],
  [3, 3, 3, 3]
];

const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

// 복사된 배열에만 변경과 추가
copy[0][0] = 99;
copy[2].push(98);

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

console.log(original);
// [ [ 99, 1, 1, 1 ], [ 0, 0, 0, 0 ], [ 2, 2, 2, 2, 98 ], [ 3, 3, 3, 3 ] ]출력
console.log(copy);
// [ [ 99, 1, 1, 1 ], [ 0, 0, 0, 0 ], [ 2, 2, 2, 2, 98 ], [ 3, 3, 3, 3 ] ]출력
```

```js
const original = [
  {
    a: 1,
    b: 2
  },
  true
];
const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

// 복사된 배열에만 변경.
copy[0].a = 99;
copy[1] = false;

console.log(JSON.stringify(original) === JSON.stringify(copy)); // false

console.log(original);
// [ { a: 99, b: 2 }, true ]
console.log(copy);
// [ { a: 99, b: 2 }, false ]
```

배열 안에 객체를 수정하고자 할 경우 얕은 복사를 수행하는 것을 볼 수 있다.<br>
하지만 원시값은 기본적으로 깊은 복사라 기존 변수에 있는 값과는 다른 값을 도출하는 것을 볼 수 있다.

```js
[Object.assign()]
= Object.assign(생성할 객체, 복사할 객체)
```

메소드의 첫 번째 인자로 빈 객체를 넣어주고 두 번째 인자로 복사할 객체를 넣어주면 된다.

```js
const object = {
  a: "a",
  number: {
    one: 1,
    two: 2
  }
};

const copy = Object.assign({}, object);

copy.number.one = 3;

console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // true
```

복사된 객체 copy 자체는 기존 object와 다른 객체지만 그 안에 들어가 있는 값은 기존 object안의 값과 같은 참조 값을 가리키고 있다.

**[Spread 연산자 (전개 연산자)]**

```js
const object = {
  a: "a",
  number: {
    one: 1,
    two: 2
  }
};

const copy = { ...object };

copy.number.one = 3;

console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // true
```

▷ **깊은 복사 (deep copy)**<br>
깊은 복사란,<br>
**'실제 값'을 새로운 메모리 공간에 복사하는 것**을 의미한다.

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj };

obj2.a = 100;

console.log(obj1 === obj2); // false
console.log(obj1.a); // 1
```

...(spread) 연산자를 통해 { }안에 obj1의 속성을 복사하여 obj2에 할당하였다.<br>
이제 obj1과 obj2는 다른 주소를 갖게되었다. (그러나 딱, 1 depth 까지만)

- **깊은 복사 방법**

```js
[JSON.parse && JSON.stringify];
```

JSON.stringify()는 객체를 json 문자열로 변환하는데 이 과정에서 원본 객체와의 참조가 모두 끊어진다.<br>
객체를 json 문자열로 변환 후, JSON.parse()를 이용해 다시 원래 객체(자바스크립트 객체)로 만들어준다.

이 방법이 가장 간단하고 쉽지만 다른 방법에 비해 느리다는 것과 객체가 function일 경우,<br>
undefined로 처리한다는 것이 단점이다.

```js
const object = {
  a: "a",
  number: {
    one: 1,
    two: 2
  },
  arr: [1, 2, [3, 4]]
};

const copy = JSON.parse(JSON.stringify(object));

copy.number.one = 3;
copy.arr[2].push(5);

console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // false
console.log(object.arr === copy.arr); // false

console.log(object); // { a: 'a', number: { one: 1, two: 2 }, arr: [ 1, 2, [ 3, 4 ] ] }
console.log(copy); // { a: 'a', number: { one: 3, two: 2 }, arr: [ 1, 2, [ 3, 4, 5 ] ] }
```

**[재귀 함수를 구현한 복사]**

복잡하다는 것이 단점,,

```js
const object = {
  a: "a",
  number: {
    one: 1,
    two: 2
  },
  arr: [1, 2, [3, 4]]
};

function deepCopy(object) {
  if (object === null || typeof object !== "object") {
    return object;
  }
  // 객체인지 배열인지 판단
  const copy = Array.isArray(object) ? [] : {};

  for (let key of Object.keys(object)) {
    copy[key] = deepCopy(object[key]);
  }

  return copy;
}

const copy = deepCopy(object);

copy.number.one = 3;
copy.arr[2].push(5);

console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // false
console.log(object.arr === copy.arr); // false

console.log(object); // { a: 'a', number: { one: 1, two: 2 }, arr: [ 1, 2, [ 3, 4 ] ] }
console.log(copy); // { a: 'a', number: { one: 3, two: 2 }, arr: [ 1, 2, [ 3, 4, 5 ] ] }
```

**[Lodash 라이브러리 사용]**

라이브러리를 사용하면 더 쉽고 안전하게 깊은 복사를 할 수 있다.<br>
설치를 해야 한다는 점과 일반적인 개발에는 효율적이겠지만,<br>
코딩 테스트에는 사용할 수 없다는 것이 단점이다.

```js
const deepCopy = require("lodash.clonedeep");

const object = {
  a: "a",
  number: {
    one: 1,
    two: 2
  },
  arr: [1, 2, [3, 4]]
};

const copy = deepCopy(object);

copy.number.one = 3;
copy.arr[2].push(5);

console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // false
console.log(object.arr === copy.arr); // false

console.log(object); // { a: 'a', number: { one: 1, two: 2 }, arr: [ 1, 2, [ 3, 4 ] ] }
console.log(copy); // { a: 'a', number: { one: 3, two: 2 }, arr: [ 1, 2, [ 3, 4, 5 ] ] }
```
