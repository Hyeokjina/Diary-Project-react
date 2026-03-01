# 오늘 한 줄 (Today's Line) 📝

하루를 한줄로 기록하는 미니멀 일기 애플리케이션

## 📁 프로젝트 구조
```
board-project/
├── public/
│   └── vite.svg
├── src/
│   ├── components/
│   │   └── common/
│   │       ├── Header.jsx              # 헤더 컴포넌트
│   │       ├── Header.styled.js        # 헤더 스타일
│   │       └── Layout.jsx              # 레이아웃 컴포넌트
│   │
│   ├── pages/
│   │   ├── Auth.styled.js              # 인증 페이지 공통 스타일
│   │   ├── Login.jsx                   # 로그인 페이지
│   │   ├── Signup.jsx                  # 회원가입 페이지
│   │   ├── Home.jsx                    # 홈 페이지
│   │   ├── DiaryList.jsx               # 일기 목록 페이지
│   │   ├── DiaryList.styled.js         # 일기 목록 스타일
│   │   ├── DiaryWrite.jsx              # 일기 작성 페이지
│   │   ├── DiaryWrite.styled.js        # 일기 작성/수정 스타일
│   │   ├── DiaryDetail.jsx             # 일기 상세/수정 페이지
│   │   ├── MyPage.jsx                  # 마이페이지
│   │   ├── Mypage.styled.js            # 마이페이지 스타일
│   │   └── NotFound.jsx                # 404 페이지
│   │
│   ├── routes/
│   │   ├── routes.jsx                  # 라우트 설정
│   │   └── routePaths.js               # 경로 상수 관리
│   │
│   ├── stores/
│   │   ├── useAuthStore.js             # 인증 상태 관리
│   │   └── useDiaryStore.js            # 일기 상태 관리
│   │
│   ├── App.jsx                         # 앱 진입점
│   ├── App.css
│   ├── main.jsx                        # React DOM 렌더링
│   └── index.css                       # 글로벌 스타일
│
├── index.html
├── package.json
├── vite.config.js
└── eslint.config.js
```

## 🗂️ 디렉토리 상세설명

### `/src/components/`
재사용 가능한 컴포넌트들을 관리합니다.

- **`common/`**: 전역적으로 사용되는 공통 컴포넌트
  - `Layout.jsx`: 모든 페이지를 감싸는 레이아웃 (헤더 포함)
  - `Header.jsx`: 네비게이션 바 및 인증 상태 표시

### `/src/pages/`
각 라우트에 대응하는 페이지 컴포넌트들입니다.

- **인증 관련**
  - `Login.jsx`: 로그인 페이지
  - `Signup.jsx`: 회원가입 페이지
  - `Auth.styled.js`: 로그인/회원가입 공통 스타일

- **일기 관련**
  - `DiaryList.jsx`: 일기 목록 조회 및 검색
  - `DiaryWrite.jsx`: 새 일기 작성
  - `DiaryDetail.jsx`: 일기 상세 조회 및 수정
  - `DiaryWrite.styled.js`: 일기 작성/수정 공통 스타일
  - `DiaryList.styled.js`: 일기 목록 스타일

- **기타**
  - `Home.jsx`: 메인 홈 페이지 (감정 통계 표시)
  - `MyPage.jsx`: 회원정보 수정 및 탈퇴
  - `NotFound.jsx`: 404 에러 페이지

### `/src/routes/`
라우팅 관련 설정을 관리합니다.

- `routes.jsx`: React Router 설정 및 라우트 정의
- `routePaths.js`: 경로 상수를 중앙 관리 (하드코딩 방지)

### `/src/stores/`
Zustand를 사용한 전역 상태 관리 스토어입니다.

- **`useAuthStore.js`**: 인증 상태 관리
  - 회원가입 (`signup`)
  - 로그인 (`login`)
  - 로그아웃 (`logout`)
  - 회원정보 수정 (`updateUser`)
  - 회원 탈퇴 (`deleteUser`)
  - 현재 사용자 정보 (`currentUser`)

- **`useDiaryStore.js`**: 일기 데이터 관리
  - 일기 추가 (`addDiary`)
  - 일기 수정 (`updateDiary`)
  - 일기 삭제 (`deleteDiary`)
  - 사용자별 일기 조회 (`getUserDiaries`)
  - 일기 검색 (`searchDiaries`)
  - 감정별 필터링 (`filterByEmotion`)

## 🎨 스타일링 구조

### Styled Components 패턴
각 페이지는 대응하는 `.styled.js` 파일을 가집니다:
```
DiaryList.jsx  ←→  DiaryList.styled.js
DiaryWrite.jsx  ←→  DiaryWrite.styled.js
Login.jsx      ←→  Auth.styled.js
Signup.jsx     ←→  Auth.styled.js (공유)
```

### 공통 스타일 공유
- `Auth.styled.js`: Login과 Signup에서 공유
- `DiaryWrite.styled.js`: DiaryWrite와 DiaryDetail에서 공유

## 🔄 데이터 흐름
```
User Action
    ↓
Component (Page/Component)
    ↓
Zustand Store (useAuthStore / useDiaryStore)
    ↓
localStorage (persist middleware)
```

## 🛣️ 라우팅 구조
```
/ (Layout)
├── / (Home)
├── /login (Login)
├── /signup (Signup)
├── /diaries (DiaryList)
├── /diaries/write (DiaryWrite)
├── /diaries/:id (DiaryDetail)
├── /mypage (MyPage)
└── /* (NotFound)
```

## 📦 주요 기술 스택

- **React 19.2.0**: UI 라이브러리
- **React Router 7.10.0**: 라우팅
- **Zustand 5.0.9**: 상태 관리
- **Styled Components 6.1.19**: CSS-in-JS 스타일링
- **Vite 7.2.4**: 빌드 도구

## 📸 대표 예시 화면

### 홈 & 인증
| 회원가입 | 로그인 | 홈 페이지 |
|----------|--------|----------|
| ![회원가입](./images/signup.PNG) | ![로그인](./images/login.PNG) | ![홈](./images/home.PNG) |

### 일기 관리
| 일기 목록 | 일기 작성 | 일기 상세/수정 |
|----------|----------|---------------|
| ![일기목록](./images/list.PNG) | ![일기작성](./images/write.PNG) | ![일기상세](./images/detail.PNG) |
