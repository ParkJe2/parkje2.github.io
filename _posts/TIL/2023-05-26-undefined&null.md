---
title: undefined와 null의 미세한 차이
categories: [TIL, JavaScript]
tags: [undefined, null] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 2주차(프로그래밍 기초)

오늘은 실업 급여 4회차 꼭 방문해서 신청해야 되는 날이라 아침부터 고용센터에 다녀왔다.<br>
대기 인원이 많을 거라 예상 했는데 생각보다 많지 않아서 다행이라 생각했지만,<br>
아무래도 처리 시간이 길어서 꽤 오래 대기했다.

점심시간이 다 되가는 시간에 돌아가게 되서 떡볶이를 사갔다.<br>
이것도 먹고 싶어 저것도 먹고 싶고 이상한 욕심에 둘이서 한 4인분은 산 것 같다 ㅎㅎ;<br>
결국 반도 못 먹고 냉장고로....오늘은 저녁도 분식일 예정..ㅎ!

## **undefined와 null의 미세한 차이**

자바스크립트에서 '없음'을 나타내는 값 두가지<br>
= undefined, null <br>
두 값의 의미는 같은 것 같지만 미세하게 다르고 사용하는 목적 또한 다르다.

▷ **undefined**

변수는 존재하나, 어떠한 값으로도 할당되지 않아 자료형이 정해지지(undefined) 않은 상태<br>

자바스크립트 엔진이 자동으로 부여하는 경우에 대해 알아보자!

자바스크립트 엔진은 사용자가 응당 어떤 값을 지정할 것이라고 예상되는 상황임에도 실제로는 그렇게 하지 않았을 때 undefined를 반환한다.<br>
다음 세 경우가 이에 해당한다.

값을 대입하지 않은 변수, 즉 데이터 영역의 메모리 주소를 지정하지 않은 식별자에 접근할 때<br>
객체 내부의 존재하지 않는 프로퍼티에 접근하려고 할 때<br>
return 문이 없거나 호출되지 않은 함수의 실행 결과

```js
var a;
console.log(a); // undefined

var obj = { a: 1 };
console.log(obj.b); // undefined

var func = function () {};
var c = func();
conosle.log(c); // undefined
```

위의 1번째 경우처럼 값을 대입하지 않은 경우에 대해 배열의 경우에는 조금 특이한 동작을 확인할 수 있다.

```js
var arr1 = [];
arr1.length = 3;
console.log(arr1); // [empty x 3]

var arr2 = new Array(3);
console.log(arr2); // [empty x 3]

var arr3 = [undefined, undefined, undefined];
console.log(arr3); // [undefined, undefined, undefined]
```

arr1, arr2의 경우 [empty x 3]이 출력되지만 undefined로 초기화한 arr3의 경우 출력값 자체가 다른것을 확인할 수 있다.<br>
이처럼 '비어있는 요소'와 'undefined를 할당한 요소'는 출력 결과부터 다르다.<br>
'비어있는 요소'는 순회와 관련된 많은 배열 메서드들의 순회 대상에서 제외된다.

```js
var arr1 = [undefined, 1];
var arr2 = [];
arr2[1] = 1;

arr1.forEach(function (v,i)) { console.log(v, i); }); // undefined 0 / 1 1
arr2.forEach(function (v,i)) { console.log(v, i); }); // 1 1

arr1.map(function(v,i) { return v + i});             // [NaN,2];
arr2.map(function(v,i) { return v + i});             // [empty,2];

arr1.filter(function(v) { return !v; });             // [undefined]
arr1.filter(function(v) { return !v; });             // []

arr1.reduce(function (p,c,i) { return p + c + i },'' ); // undefined011
arr1.reduce(function (p,c,i) { return p + c + i },'' ); // 11
```

arr2의 경우 각 메서드들이 비어있는 요소에 대해서는 어떠한 처리도 하지 않고 건너뛰었음을 알 수 있다.<br>
이러한 동작이 배열에서만 발견할 수 있는 특별한 현상인 것처럼 소개했지만, 사실은 배열도 객체임을 생각해보면 지극히 자연스러운 현상이다.

undefined의 경우 그 자체로 값이다.<br>
비록 '비어있음'을 의미하긴 하지만 하나의 값으로 동작하기 때문에 이때의 프로퍼티나 배열의 요소는 고유의 키값이 실존하며 순회의 대상이 될 수 있다.<br>
한편 사용자가 아무것도 하지 않은 채로 접근했을 때 자바 스크립트 엔진이 하는 수 없이 반환해주는 undefined는 해당 프로퍼티 내지 배열의 키값 자체가 존재하지 않음을 의미한다.<br>
값으로써 어딘가에 할당된 undefined는 실존하는 데이터인 반면 자바스크립트 엔진이 반환해주는 undefined는 무나 그대로 값이 없을음 나타내는 것이다.

'var a' 라는 구문에 의해 식별자 a에 자동으로 undefined가 '할당된다'고 소개하는 것이 일반적이다.<br>
그런데 자바스크립트가 실제로 그렇게 동작하는 것은 아니다.<br>
정확히는 아무것도 할장하지 않고 끝나며, 이후 변수 a에 접근하고자 할 때 비로소 undefined를 반환하는 것이 맞다.

▷ **null**

같은 의미를 가진 null이라는 값이 별도로 있는데 굳이 undefined를 써야 할 이유가 없다.<br>
'비어있음'을 명시적으로 나타내고 싶을 때는 undefined가 아닌 null을 쓰면 된다. null은 애초부터 이런 용도로 만든 데이터 타입이다.<br>
이런 규칙을 따르는 한 undefined는 오직 '값을 대입하지 않은 변수에 접근하고자 할 때 자바스크립트 엔진지 반환해주는 값'으로서만 존재할 수 있다.

null은 한 가지 주의할 점이 있는데 typeof null이 object라는 점이다.<br>
이는 자바스크립트 자체의 버그로 어떤 변수의 값이 null인지 여부를 판별하기 위해서는 typeof 대신 다른 방법으로 접근해야 한다.

```js
var n = null;
console.log(typeof n); // object

console.log(n == undefined); // true
console.oog(n == null); // true

console.log(n === undefined); // false
console.log(n === null); // true
```

저녁 시간에 개인 과제 발제가 진행되었다......<br>
다음주 목요일까지 기한이고, 해설까지 진행된다 해서 문제를 내주시는 줄 알았는데<br>
프로젝트였다니... 상상도 못했다 ㅠㅠㅠㅠㅠㅠㅠ<br>
다음주 월요일이 공휴일이라서 이번주는 주말에도 좀 쉴 계획이였는데<br>
쉬지 못할 것 같다 ㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠㅠ
