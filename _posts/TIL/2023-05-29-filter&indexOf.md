---
title: filter() & indexOf()
categories: [TIL, JavaScript]
tags: [filter, indexOf] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 3주차(프로그래밍 기초)

⭐️공휴일은 쉽니다!!!!!⭐️

But,,<br>
개인 과제를 위해 오늘도 pc앞에.....ㅎ<br>
구현해야 하는 기능에 대해 공부하다 알게 된 "filter" 와 "indexOf"는 꼭 정리해두는게 좋을 것 같아 겸사겸사 til을 쓴다!

## **filter**

배열에 주로 사용되며, **조건에 일치하는 모든 요소를 모아 새로운 배열로 반환**한다.

### **예제1) 'number'에서 5를 찾아 반환하기**

```js
const number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const value = number.filter((val) => val == 5);
console.log(value); // [5]
```

### **예제2) 'number'에서 5보다 큰 수를 찾아 반환하기**

```js
const number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const value = number.filter((val) => val > 5);
console.log(value); // [6, 7, 8, 9, 10]
```

### **예제3) 'cats'에서 'munji'를 찾아 반환하기**

```js
const cats = ["munji", "hyuji", "jerry", "tom"];
const value = cats.filter((val) => val === "munji");
console.log(value); // ['munji']
```

## **indexOf**

```js
- 문자열에서 특정 문자를 찾고, 검색된 문자열의 '첫번째'로 나타나는 위치 index를 리턴한다.
- 파라미터
 : searchvalue = 필수 입력값, 찾을 문자열
 : position = optional, 기본값은 0, string에서 searchvalue를 찾기 시작할 위치
- 찾는 문자열이 없으면 -1을 리턴한다.
- 문자열을 찾을 떄 대소문자를 구분한다.
```

### **예제1)**

```js
const str = "parkjei";
console.log(str.indexOf("pa")); // 0
// 문자열 'parkjei'에서 'pa'가 처음으로 나타나는 위치의 index값 = 0
console.log(str.indexOf("kr")); // 1
// 문자열 'parkjei'에서 'kr'이 처음으로 나타나는 위치의 index값 = 1
console.log(str.indexOf("in")); // -1
// 문자열 'parkjei'에는 'in' 문자열이 없으므로 -1을 리턴
console.log(str.indexOf("KR")); // -1
// 문자열 'parkjei'에는 'kr' 문자열이 없으므로 -1을 리턴 (대소문자 구분)
```

### **예제2) position 값을 입력한 경우**

```js
const str = "jeijei";
console.log(str.indexOf("je")); // 0
// indexOf 함수의 두번째 파라미터인 position값이 입력되지 않으면 positon 값은 0으로 처리됨
// 'jeijei' 문자열의 0번째 index부터 'je'문자열을 찾고, 0번째 index에서 문자열 'je'를 발견하였기에 0을 리턴
console.log(str.indexOf("je", 1)); // 3
// posion 값 1
// 'jeijei' 문자열의 1번째 index부터 'je'를 검색하기에 index 0에 있는 'je'를 무시하여 3을 리턴
```
