---
title: supabase List all buckets
categories: [TIL, JavaScript]
tags: [JavaScript, TypeScript, supabase] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### List all buckets

#### 버킷 목록 불러오기
```tsx
const { data, error } = await supabase
  .storage
  .listBuckets()
```
