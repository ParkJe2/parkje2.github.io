---
title: TypeScript interface
categories: [TIL, TypeScript]
tags: [TypeScript, interface] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### interface 기본 선언 및 사용 방법
```tsx
// interface 인터페이스 이름 {
//   key: type;
//   key: type;
//   key: type;

interface User {
  name: string,
  age:number
}

const user:UserInfo = {
  name: "test",
  age: 20,
}
console.log(user.name) // test
}
```

### interface optional, readonly, index 선언 및 사용 방법
- optional : 있어도 되고 없어도 되는..(= 물음표)
- readonly : 읽기 전용
- index : 여러 속성 정보를 받을 때 사용 (key:number, value: string)

```tsx
enum Gender {
    Man,
    Woman
}

interface User {
    name: string;
    age: number;
    gender?: Gender;
    readonly birth: number; 
    [key:number]: string;
}

// gender 포함
const user1:User = {
    name: "test1",
    age: 20,
    gender: Gender.Man,
    birth: 20230101,
}

// gender 제외
const user2:test2 = {
    name: "ryan2",
    age: 22,
    birth:20220101,
}

//index 사용
const user3:UserInfo = {
    name: "test3",
    age: 24,
    birth:20210101,
    1: "1반",
    2: "2번"
}
```