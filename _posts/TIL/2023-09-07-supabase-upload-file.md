---
title: supabase Upload a file
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Upload a file

#### 파일 업로드
```tsx
const avatarFile = event.target.files[0]
const { data, error } = await supabase
  .storage
  .from('avatars')
  .upload('public/avatar1.png', avatarFile, {
    cacheControl: '3600',
    upsert: false
  })
```

#### base64 파일 데이터에서 `ArrayBuffer`를 사용하여 파일 업로드
```tsx
import { decode } from 'base64-arraybuffer'

const { data, error } = await supabase
  .storage
  .from('avatars')
  .upload('public/avatar1.png', decode('base64FileData'), {
    contentType: 'image/png'
  })
```
