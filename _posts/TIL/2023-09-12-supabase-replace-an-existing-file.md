---
title: supabase Replace an existing file
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Replace an existing file

#### 기존 버킷 파일 바꾸기
```tsx
const avatarFile = event.target.files[0]
const { data, error } = await supabase
  .storage
  .from('avatars')
  .update('public/avatar1.png', avatarFile, {
    cacheControl: '3600',
    upsert: true
  })
```

#### base64 파일 데이터에서 'ArrayBuffer'를 사용하여 파일 업데이트
```tsx
import {decode} from 'base64-arraybuffer'

const { data, error } = await supabase
  .storage
  .from('avatars')
  .update('public/avatar1.png', decode('base64FileData'), {
    contentType: 'image/png'
  })
```
