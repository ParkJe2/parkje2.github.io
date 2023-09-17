---
title: supabase Upsert data
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Upsert data

#### 데이터 업로드
```tsx
const { data, error } = await supabase
  .from('countries')
  .upsert({ id: 1, name: 'Albania' })
  .select()
```

#### 여러개의 데이터 업로드
```tsx
const { data, error } = await supabase
  .from('countries')
  .upsert([
    { id: 1, name: 'Albania' },
    { id: 2, name: 'Algeria' },
  ])
  .select()
```

#### 제약 조건이 있는 테이블에 업로드
```tsx
const { data, error } = await supabase
  .from('users')
  .upsert({ id: 42, handle: 'saoirse', display_name: 'Saoirse' }, { onConflict: 'handle' })
  .select()
```
