---
title: react-paginate을 활용하여 pagination 구현하기
categories: [TIL, React]
tags: [react-paginate, pagination]# TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - Team Project

### paginate 사용하기

1. react-paginate 설치하기
```
yarn add react-paginate
```

2. 페이지 네이션 구현할 컴포넌트에 임포트
```jsx
import ReactPaginate from 'react-paginate';
```

3. 커스텀하여 사용하기
- pageCount - 총 게시글의 개수(총 row 수)
- pageRangeDisplayed - 한 페이지에 표시할 게시글의 수
- breakLabel - 페이지 수가 많을 경우 건너뛸 수 있는 버튼
- previousLabel - 이전페이지로 가는 버튼의 value값
- nextLabel - 다음페이지로 가는 버튼의 value값
- onPageChange - 페이지 버튼을 눌렀을 때 일어나는 이벤트 이를 이용해 페이지 증감
- containerClassName - css 적용할 때 사용
- activeClassName - 현재 페이지에 css처리해주기 위한 클래스명
- previousClassName/NextClassName - 이전/다음버튼 css 적용위한 클래스명


 ```jsx
 <ReactPaginate 
    pageCount={Math.ceil(totalRecords / 10)}
    pageRangeDisplayed={5}
    breakLabel={""}
    previousLabel={"<"}
    nextLabel={">"}
    onPageChange={changePage}
    containerClassName={"paginationUl"}
    activeClassName={"currentPage"}
    previousClassName={"pageLabelBtn"}
    nextClassName={"pageLabelBtn"}
/>  
 ```