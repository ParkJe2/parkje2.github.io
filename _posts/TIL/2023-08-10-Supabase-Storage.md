---
title: Supabase Storage 사용하기
categories: [TIL, React]
tags: [supabase, storage] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - Team Project

### Supabase Storage
- 스토리지 파일 업로드
```js
import { createClient } from '@supabase/supabase-js'

// Supabase client 생성
const supabase = createClient('your_project_url', 'your_supabase_api_key')

// 파일 업로드
async function uploadFile(file) {
  const { data, error } = await supabase.storage.from('bucket_name').upload('file_path', file)
  if (error) {
    // Handle error
  } else {
    // Handle success
  }
}
```
