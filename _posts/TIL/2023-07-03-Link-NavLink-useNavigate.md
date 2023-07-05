---
title: Link, NavLink, useNavigate
categories: [TIL, React]
tags: [React, Link, NavLink, useNavigate] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 7주차(주특기 심화 - React)

### **리액트 라우터 설치**

Link와 useNavigate()를 사용하기 위해선 우선, 리액트 라우터를 설치해야 한다.
```bash
// for yarn
$ yarn add react-router-dom@6

// for npm
$ npm install react-router-dom@6
```

### **Link**
```jsx
import { Link } from "react-router-dom";
<Link to="경로">내용</Link>
```
```jsx
import { Routes, Route, Link } from "react-router-dom";
import Home from './Home';
import Login from './Login';

function App() {
  return (
    <div>
      <ul>
        <li><Link to="/home">Home</Link></li>
        <li><Link to="/login">Login</Link></li>
      </ul>
      <Routes>
        <Route path="/home" element={<Home />}></Route>
        <Route path="/login" element={<Login />}></Route>
      </Routes>
    </div>
  );
}

export default App;
```

react-router-dom 에서 제공하는 컴포넌트는 html의 \<a> 태그와 기능이 유사하지만, 페이지 전환을 방지하는 기능이 내장되어 있다. 

요소 클릭 시 <도메인 경로> / <지정한경로> 로 바로 이동하는 로직 구현 시에 용이한 컴포넌트이다. 

### **NavLink**

```jsx
import { NavLink } from "react-router-dom";

// style 속성으로 스타일 적용할 때
<NavLink to="경로" style={({isActive}) => ({
	css속성: isActive ? '활성화 되었을 때 스타일' : '비활성화 스타일',
    ...
    })}>
    내용
</NavLink>


// className 속성으로 스타일 적용할 때 
<NavLink to="경로" className={({isActive}) => {
	return isActive ? '클래스명' : '';
    }}>
    내용
</NavLink>
```

\<NavLink>는 \<Link>의 speicial version으로, 특정 링크에 스타일을 넣어줄 수 있다. 

기존의 activeStyle과 activeClassName 속성은 삭제되어 더 이상 사용할 수 없다.

activeStyle은 style로 activeClassName은 className 변경되었다.

NavLink는 자체적으로 isActive라는 boolean값을 가지고 있어 선언하여 활성화시키고 싶은 스타일에 css를 적용할 수 있다.

활성화(클릭) 시 해당 요소의 클래스는 "active"로 변경된다.

```jsx
// src/App.css
.orange {
  color: orange;
  font-weight: bold;
}


// src/App.jsx
import './App.css';
import { Routes, Route, Link, NavLink } from "react-router-dom";
import Home from './Home';
import Login from './Login';

const activeStyle = {
  color: 'red',
  textDecoration: 'underline'
}
const deactiveStyle = {
  color: 'black',
  textDecoration: 'none'
}

function App() {
  
  return (
    <div>
      <p>
        // style 속성
        <NavLink to="/home" style={({isActive}) => {
          return isActive ? activeStyle : deactiveStyle;
        }}>Home</NavLink>
      </p>
      <p>
        // className 속성
        <NavLink to="/login" className={({isActive}) => {
          return isActive ? 'orange' : '';
        }}>Login</NavLink>
      </p>
      <hr />
      <Routes>
        <Route path="/home" element={<Home />}></Route>
        <Route path="/login" element={<Login />}></Route>
      </Routes>
    </div>
  );
}

export default App;
```

### **useNavigate**
```jsx
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();
navigate('경로');
```

useNavigate 훅을 실행하면 페이지 이동을 할 수 있게 해주는 함수를 반환한다.

반환받은 함수의 인자로 설정한 경로를 넘겨주면 해당 경로로 이동할 수 있다.

Link와 다른 점은 함수 호출을 통해 페이지를 이동하기 때문에 특정 조건을 충족할 경우에 페이지 이동을 하도록 할 수 있다. 

```jsx
import { Routes, Route, useNavigate } from "react-router-dom";
import Home from './Home';
import Login from './Login';
import { useState } from 'react';
function App() {
  const [text, setText] = useState('');
  const navigate = useNavigate();

  const goHome = () => {
    setText('Home 페이지 입니다.')
    navigate('/home');
  }
  const goLogin = () => {
    setText('Login 페이지 입니다.')
    navigate('/login');
  }
  return (
    <div>
      <p>{text}</p>
      <button type="button" onClick={goHome}>Home</button>
      <button type="button" onClick={goLogin}>Login</button>
      <Routes>
        <Route path="/home" element={<Home />}></Route>
        <Route path="/login" element={<Login />}></Route>
      </Routes>
    </div>
  );
}

export default App;
```