---
title: supabase Fetch data
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Fetch data

#### 데이터 가져오기
```tsx
const { data, error } = await supabase
.from('countries')
.select()
```

#### 특정 column 데이터 가져오기
```tsx
const { data, error } = await supabase
.from('countries')
.select('name')
```

#### 특정 데이터 가져오기
```tsx
const { data, error } = await supabase
  .from('countries')
  .select()
  .eq('name', 'Albania')
```

#### 특정 데이터 제외 가져오기
```tsx
const { data, error } = await supabase
  .from('countries')
  .select()
  .neq('name', 'Albania')
```
