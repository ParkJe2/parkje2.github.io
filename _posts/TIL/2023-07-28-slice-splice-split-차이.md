---
title: slice(), splice(), split()의 차이
categories: [TIL, JavaScript]
tags: [JavaScript, slice, splice, split] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### slice()
- 원본 유지 / 원하는 부분을 복사하여 새로운 배열로 리턴
```js
// slice(시작, 끝)

let slice_array = ['1', '2', '3', '4'];
new_array = slice_array.slice(2,3) 
console.log(new_array) // ['3' , '4']
```

### splice()
- 원본 수정
```js
// splice(시작, 잘라낼 갯수, 추가할 요소)

// 요소 제거
let splice_array = ['1', '2', '3', '4'];
splice_array.splice(1,3) 
console.log(splice_array) // ['1']

// 요소 제거 후 새로운 요소 추가
let splice_array = ['1', '2', '3', '4'];
splice_array.splice(1,3, '5', '6') 
console.log(splice_array) // ['1', '5', '6']

// 새로운 요소 추가
let splice_array = ['1', '2', '3', '4'];
splice_array.splice(1,0,'5', '6')
console.log(splice_array) // ['1', '2', '3', '4', '5', '6']
```

### split()
- 원본 유지 / 문자열을 다루는 메서드
- 구분 문자를 기준으로 잘린 배열을 반환

```js
// split("구분 문자")

// 공백으로 나누기
const split_string = "Nice to meet you";
split_array = split_string.split(" ")
console.log(split_array) // ['Nice', 'to', 'meet', 'you']

// 모든 문자로 나누기
const split_string = "Nice to meet you";
split_array = split_string.split("")
console.log(split_array) // ['N', 'i', 'c', 'e', ' ', 't', 'o', ' ', 'm', 'e', 'e', 't', ' ', 'y', 'o', 'u']
```