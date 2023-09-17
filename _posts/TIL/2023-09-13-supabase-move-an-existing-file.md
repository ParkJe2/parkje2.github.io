---
title: supabase Move an existing file
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Move an existing file

#### 기존 파일 이동하기
```tsx
const { data, error } = await supabase
  .storage
  .from('avatars')
  .move('public/avatar1.png', 'private/avatar2.png')
```
