## 카카오 검색(책) API를 활용한 비동기 통신 실습

## 📁 프로젝트 구조

```
book-search/
├── index.html
├── style.css
└── script.js
```

## API 명세

- 카카오 API 문서: https://developers.kakao.com/docs/latest/ko/daum-search/dev-guide#search-book

```
// 카카오 책 검색 API 정보
URL: https://dapi.kakao.com/v3/search/book
Method: GET
Headers: Authorization: KakaoAK {API_KEY}
Parameters:
  - query: 검색어 (필수)
  - size: 결과 개수 (기본 10개)
```

## TODO

1. searchBooks 함수 구현
2. 폼 이벤트 처리
3. 렌더링 함수
