---
title: supabase Empty a buckets
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Empty a buckets

#### 버킷 비우기
```tsx
const { data, error } = await supabase
  .storage
  .emptyBucket('avatars')
```
