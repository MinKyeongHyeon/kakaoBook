# 카카오 검색(책) API를 활용한 비동기 통신 실습 - 2회차

## 🎯 학습 목표

- API 페이지네이션 파라미터 활용
- 상태 관리를 통한 페이지 정보 추적
- 동적 UI 생성 및 조건부 렌더링
- 사용자 경험을 고려한 페이지 이동 기능

## 📁 프로젝트 구조

```
book-search-pagination/
├── index.html
├── style.css
└── script.js
```

## 🔄 1회차 → 2회차 변경사항

- **HTML**: `<div id="pagination"></div>` 컨테이너 추가
- **CSS**: 페이지네이션 버튼 스타일링 추가
- **JavaScript**: 상태 관리 및 페이지네이션 로직 구현

## 📝 TODO

- 1단계: 상태 관리 변수 선언
- 2단계: searchBooks 함수 수정
- 3단계: renderPagination 함수 구현

## 🚀 실습 진행 순서

1. JavaScript 단계별 구현: TODO 주석 따라 구현
2. 기능 테스트: 검색 → 페이지 이동 → 새로운 검색 순서로 테스트

## 📡 API 명세

- 카카오 API 문서: https://developers.kakao.com/docs/latest/ko/daum-search/dev-guide#search-book

```bash
# 카카오 책 검색 API 정보 (페이지네이션 포함)
URL: https://dapi.kakao.com/v3/search/book
Method: GET
Headers: Authorization: KakaoAK {API_KEY}
Parameters:
  - query: 검색어 (필수)
  - page: 페이지 번호 (기본 1, 최대 50)
  - size: 결과 개수 (기본 10개, 최대 50개)
```

## 📊 API 응답 구조

```json
{
  "documents": [
    {
      "title": "책 제목",
      "authors": ["저자1", "저자2"],
      "thumbnail": "이미지 URL",
      "publisher": "출판사",
      "price": 15000
    }
  ],
  "meta": {
    "total_count": 2000, // 전체 검색 결과 수
    "pageable_count": 1000, // 페이지네이션 가능한 결과 수
    "is_end": false // 마지막 페이지 여부
  }
}
```

### 페이지 범위 계산

```javascript
const startPage = Math.max(1, currentPage - 2);
const endPage = Math.min(totalPages, startPage + 4);
```

### 총 페이지 수 계산

```javascript
totalPages = Math.min(50, Math.ceil(data.meta.pageable_count / 10));
```
