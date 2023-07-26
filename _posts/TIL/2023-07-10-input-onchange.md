---
title: input & onChange
categories: [TIL, React]
tags: [React, input, onChange] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 8주차(주특기 심화 - React)

### useState의 응용 (input의 onChange)
input 태그의 onChange는 input태그에 글자를 입력할 때 발생하는 이벤트이다.

예제) 리액트에서 input태그 값 가져오기
```jsx
<input onChange={(event) => { console.log(event.target.value) }}/>
```

예제) 리액트에서 input태그 값 저장하기
```jsx
function App() {
  const [value, setValue] = useState(""); // 1. state 선언
  console.log(value); // 3. value 계속 변경
  return <input onChange={(e) => setValue(e.target.value)} />; // 2. input 값 입력 때마다 value 변경
}
```

예제3) input 입력 값 alert창으로 띄우기 (* state(value)에 입력한 값이 항상 저장됨)
```jsx
function App() {
  const [value, setValue] = useState("");
  return (
    <>
      <input onChange={(e) => setValue(e.target.value)} />
			// 버튼을 추가하여 클릭 시 현재 value를 알림창에 띄우기
      <button
        onClick={() => {
          alert(value);
        }}
      >
        입력한 값을 알림창에 띄우기
      </button>
    </>
  );
}
```