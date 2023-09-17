---
title: supabase Delete a buckets
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Delete a buckets

#### 버킷 삭제하기
```tsx
const { data, error } = await supabase
  .storage
  .deleteBucket('avatars')
```
