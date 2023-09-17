---
title: supabase Download a file
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Download a file

#### 파일 다운로드
```tsx
const { data, error } = await supabase
  .storage
  .from('avatars')
  .download('folder/avatar1.png')
```

#### 파일 변환하여 다운로드
```tsx
const { data, error } = await supabase
  .storage
  .from('avatars')
  .download('folder/avatar1.png', {
    transform: {
      width: 100,
      height: 100,
      quality: 80
    }
  })
```
