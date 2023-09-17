---
title: supabase Insert data
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Insert data

#### 데이터 생성하기
```tsx
const { error } = await supabase
.from('countries')
.insert({ id: 1, name: 'Denmark'})
```

#### 데이터 생성 및 반환하기
```tsx
const { data, error } = await supabase
.from('countries')
.insert({ id: 1, name: 'Denmark'})
.select()
```

#### 여러개의 데이터 생성하기
```tsx
const { error } = await supabase
.from('countries')
.insert([
  {id: 1, name: 'Nepal'},
  {id:1, name: 'Vietnam'}
])
```
