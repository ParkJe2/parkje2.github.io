---
title: supabase Delete data
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Delete data

#### 데이터 삭제
```tsx
const { error } = await supabase
  .from('countries')
  .delete()
  .eq('id', 1)
```
