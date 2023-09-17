---
title: supabase maybeSingle
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### maybeSingle

supabase의 .single()은 반환 값이 1개가 아닐 경우 error를 반환한다.<br/>
.limit(1)을 활용할 수 있다.

```jsx
const {data, error} = await supabase
.from("users")
.eq("number", 1)
.single();

if(error) throw error;
data;
```

특정한 값을 조회할 때는 maybeSingle()을 활용하면 된다.</br>
(반환된 데이터가 배열 형태가 아님)

```jsx
const {data, error} = await supabase
.from("users")
.eq("number", 1)
.maybeSingle();

if(error) throw error(500);
data; // {} || null
```
