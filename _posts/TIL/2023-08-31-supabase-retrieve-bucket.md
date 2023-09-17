---
title: supabase Retrieve a bucket
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Retrieve a bucket

#### 버킷 가져오기
```tsx
const { data, error } = await supabase
  .storage
  .getBucket('avatars')
```
