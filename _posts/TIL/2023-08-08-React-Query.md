---
title: React-Query 기본 사용법
categories: [TIL, React]
tags: [React-Query, useQuery, useMutation] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - Team Project

### React-Query
- 사용자에게 새로운 정보를 보여줄 수 있는 옵션을 제공한다.

#### Remount
- 컴포넌트 또는 페이지를 다시 마운트 했을 때 새로운 데이터 갱신
- refetchOnMount 옵션을 통해 설정 (default 값 = true)

#### Window refocus
- 윈도우 창을 다시 포커스 할 때 새로운 데이터를 갱신
- refetchOnWindowFocus 옵션을 통해 설정 (default 값 = true)

#### Network reconnect
- 네트워크가 다시 연결되면 새로운 데이터를 갱신
- refetchOnReconnect 옵션을 통해 설정 (default 값 = true)

#### useQuery
- HTTP GET 요청을 할 때, 주로 사용
- queryKey, queryFn, options를 이용해서 코드를 작성할 수 있음

#### useMutation
- 서버의 데이터를 변경할 때 사용 (HTTP POST, PUT, DELETE)
