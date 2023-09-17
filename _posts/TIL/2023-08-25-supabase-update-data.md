---
title: supabase Update data
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Update data

#### 데이터 업데이트
```tsx
const { error } = await supabase
.from('countries')
.update({ name: 'Australia'})
.eq('id', 1)
```

#### 데이터 업데이트 및 반환
```tsx
const { data, error } = await supabase
.from('countries')
.upate({ name: 'Australia'})
.eq('id', 1)
.select()
```

#### JSON 데이터 업데이트
```tsx
const { data, error } = await supabase
  .from('users')
  .update({
    address: {
      street: 'Melrose Place',
      postcode: 90210
    }
  })
  .eq('address->postcode', 90210)
  .select()
```
