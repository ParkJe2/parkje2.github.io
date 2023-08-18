---
title: Supabase Session
categories: [TIL, TypeScript]
tags: [TypeScript, Supabase, Session] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 최종 프로젝트 주차 - Team Project

### Supabase Session

#### 세션 검색
- 세션 데이터 가져오기
```jsx
const { data, error } = await supabase.auth.getSession()
```

#### 새 세션 검색
- 현재 세션을 사용하여 세션 새로 고침
```jsx
const { data, error } = await supabase.auth.refreshSession()
const { session, user } = data
```

#### 새로 고침 토큰을 사용하여 새션 새로 고침
```jsx
const { data, error } = await supabase.auth.refreshSession({ refresh_token })
const { session, user } = data
```

#### 사용자 검색
- 현재 기존 세션으로 로그인한 사용자 가져오기
```jsx
const { data: { user } } = await supabase.auth.getUser()
```

- 사용자 정의 엑세스 토큰 jwt로 로그인한 사용자 가져오기
```jsx
const { data: { user } } = await supabase.auth.getUser(jwt)
```

#### 사용자 업데이트
- 인증된 사용자의 이메일 업데이트
```jsx
const { data, error } = await supabase.auth.updateUser({email: 'new@email.com'})
```

- 인증된 사용자의 비밀번호 업데이트
```jsx
const { data, error } = await supabase.auth.updateUser({password: 'new password'})
```

- 사용자의 메타데이터 업데이트
```jsx
const { data, error } = await supabase.auth.updateUser({
  data: { hello: 'world' }
})
```

#### 세션 데이터 설정
- 세션 새로고침
```jsx
  const { data, error } = supabase.auth.setSession({
    access_token,
    refresh_token
  })
```