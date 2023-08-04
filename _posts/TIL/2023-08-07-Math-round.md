---
title: Math.round()
categories: [TIL, JavaScript]
tags: [JavaScript, Math.round()] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### Math.round()
- 가장 가까운 정수로 반올림한 숫자 값을 반환하는 메서드
- Math 객체의 round() 메서드를 사용하는 방법
- round() 메서드는 Math 객체와 같이 사용되어야 함

```js
console.log(Math.round(0.9));
//  1
console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05));
// 6 6 5
console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95));
// -5 -5 -6
```

