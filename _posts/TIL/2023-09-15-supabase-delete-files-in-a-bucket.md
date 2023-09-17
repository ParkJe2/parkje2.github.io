---
title: supabase Delete files in a bucket
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Delete files in a bucket

#### 버킷 파일 삭제
```tsx
const { data, error } = await supabase
  .storage
  .from('avatars')
  .remove(['folder/avatar1.png'])
```
