---
title: localStorage list 정렬
categories: [TIL, JavaScript]
tags: [localStorage] # TAG names should always be lowercase
---

## 내일배움캠프 LGLG!

### 4주차(프로그래밍 기초)

리뷰 페이지 구현을 마치고 테스트를 하던 중 거슬리는 부분이 생겼다..!<br>
바로 작성된 댓글 노출 순서였는데..<br>
작성순, 최신순이 아니라 뒤죽박죽으로 등록되고 있었다..ㅠㅠ<br>
최신순으로 노출되게 구현하고 싶어 여러 방법을 찾아봤는데 생각보다 잘 되지 않았다.<br>
파이썬에서 댓글 구현 했을 땐 sort를 사용해서 쉽게 성공을 했었는데..<br>
포기할까 여러번 고민했지만,, 여러 시도 끝에 드디어 성공했다ㅎㅎㅎㅎ!

## **localStorage list 정렬**

![Desktop View](til/etc/data.png)
_로컬스토리지에 저장된 리뷰 작성 내용_

먼저, 콘솔에 localStorage를 찍어보니 저장된 데이터가 **배열을 둘러싸지 않은 객체로 출력** 되었다.

```js
console.log(localStorage);
```

![Desktop View](til/etc/localstagetest.png)
_출력 내용_

두번째로, localstorage[키]를 넣어 출력해 보았다.

```js
console.log(localStorage["a1bd67a9-1910-423c-8f23-4e82151f5ed1"]);
```

![Desktop View](til/etc/keytest.png)
_출력 내용_

여기까지 확인했을 때 "오! 이렇게 접근이 가능하구나! 곧 해결할 수 있겠다." 라고 생각했지만..<br>
진짜 너무너무 오래 걸렸다 ㅠㅠㅠㅠㅠ

다음은 키를 **배열로 불러오기 위해 Object.keys()를 사용**했다.

- **Object.keys()** - 주어진 객체의 속성 이름들을 일반적인 반복문과 동일한 순서로 순회되는 열거할 수 있는 배열로 반환해주는 메서드

```js
console.log(Object.keys(localStorage));
```

![Desktop View](til/etc/objectkeys.png)
_출력 내용_

정상적으로 불러와지는 것을 보고 기뻤지만,,<br>
**forEach로 돌릴 수 없는 상태이기 때문에 새 객채로 반환받기 위해 map()을 사용**했다..

- **map()**

* 키(key)가 있는 데이터를 저장한다는 점에서 객체(Object)와 유사하다.
* 키(key)에 다양한 자료형을 허용한다.
* 객체(Object)와 달리 키(key)를 문자형으로 타입 변환 없이 그대로를 유지한다.
* NaN도 키(key)로 사용 가능하다.
* 값(value)의 삽입 순서를 기억한다. (객체는 프로퍼티 순서를 기억하지 못함)
* 배열(Array)와 유사하게 내장 메서드 forEach도 지원한다.

```js
console.log(
  Object.keys(localStorage).map((l) => ({
    ...JSON.parse(localStorage.getItem(l)),
    key: l
  }))
);
//
```

![Desktop View](til/etc/map.png)
_출력 내용_

진짜...... 출력된 거 보고 소리 지를 뻔...ㅠㅠㅠㅠㅠㅠ

이제...**최신순으로 정렬시키기 위해 sort()를 사용**할 차례다! (도대체 언제 끝남..)

- **sort()** - 배열의 요소를 정렬하는데 사용<br>

```js
const String = ["b", "c", "a"];
console.log(String.sort()); // a, b, c
```

- **sort 함수 응용**

```js
const numbers = [0, 5, 4, 1, 2];
numbers.sort((a, b) => a - b); // 오름차순
```

- 반환 값 < 0 : a가 b보다 앞에 있어야 한다.
- 반환 값 = 0 : a와 b의 순서를 바꾸지 않는다.
- 반환 값 > 0 : b가 a보다 앞에 있어야 한다.

내가 구현한 리뷰 작성 데이터에는 작성 시간을 가지고 있기 때문에<br>
작성한 시간을 기준으로 최신순 정렬을 시도했다.

```js
console.log(
  Object.keys(localStorage)
    .map((l) => ({ ...JSON.parse(localStorage.getItem(l)), key: l }))
    .sort((a, b) => new Date(b.date) - new Date(a.date))
);
```

![Desktop View](til/etc/sort.png)
_출력 내용_

- **테스트 도중 다른 작업하다 이전 작성한 댓글을 삭제하여 다시 등록된 점 참고 부탁드립니다.**
- **new Date()는 기본적으로 미국시간을 기준으로 하여 해당 출력물에선 시간이 다르게 보입니다..!**

드디어 성공~!!!<br>
[완성 코드]

```js
Object.keys(localStorage)
  .map((l) => ({ ...JSON.parse(localStorage.getItem(l)), key: l }))
  .sort((a, b) => new Date(b.date) - new Date(a.date))
  .forEach((data) => {
    if (data.movieId === movieId) {
      reviewList.innerHTML += `<div class="list-box">
    <p class="list-text">${data.reviewText}</p>
    <h5 class="list-title">⎯ ${data.nickname}</h5>
    <p class="list-time">작성시간 : ${new Date(data.date).toLocaleString(
      "ko-KR"
    )}</p>
    </div>`;
    }
  });
```

귀찮지만,, 정렬 기능이 정확히 구현된 부분을 기록하고 싶기에 코드를 되돌리고 테스트 리뷰 몇개를 더 작성해보았다..!

**(중요)** 코드를 되돌려서 테스트 리뷰 작성 이 후 코드 적용을 하였기에 구현 후 이미지에선 작성 시간 데이터가 깨져 보이는 점 참고 부탁드립니다!!
(기능 구현 적용된 코드에서 새로 작성한 리뷰는 시간 잘 불러와 짐!)

![Desktop View](til/etc/before.png)
_최신순 정렬 기능 구현 전_

![Desktop View](til/etc/after.png)
_최신순 정렬 기능 구현 후_

오늘은 좀 뿌듯하고 싶다!!!!!!!!!!!!!
