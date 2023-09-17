---
title: supabase Copy an existing file
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Copy an existing file

#### 기존 파일 복사하기
```tsx
const { data, error } = await supabase
  .storage
  .from('avatars')
  .copy('public/avatar1.png', 'private/avatar2.png')
```
