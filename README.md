# Focus Dash

<img width="800" alt="FocusDash-reports" src="https://github.com/user-attachments/assets/8e214df1-ef06-4126-bf53-7090b5b6ac06" />

> 프리랜서를 위한 프로젝트 업무 관리 및 오버워킹 방지 솔루션

작업 시간을 단순히 기록하는 것을 넘어,
예상 시간과 실제 작업 시간을 비교하여 반복적인 초과 작업 패턴을 분석하고
오버워킹을 예방하는 생산성 관리 서비스입니다.

## 프로젝트 개요

- 기간 : 2025.10 ~ 2026.04
- 인원 : FE 3 / BE 2 / Server 1
- 역할 : Frontend Leader


## 핵심 목표

기존 작업 관리 도구는 단순 일정 관리에 집중되어 있어
"실제 작업 시간"과 "예상 시간" 사이의 차이를 분석하기 어렵다는 문제를 발견했습니다.

Focus Dash는 다음 문제를 해결하고자 했습니다.

- 프로젝트 단위를 세분화하여 작업 관리  
- 예상 시간과 실제 작업 시간 비교  
- 반복되는 초과 작업 패턴 데이터화  
- 오버워킹 예방 및 견적 정확도 향상

---

## 기술 스택

### Frontend

- Next.js
- TypeScript
- Zustand
- TanStack Query
- React Hook Form
- Zod
- Axios
- Tailwind CSS
- shadcn/ui
- Chart.js

### Backend / Infra

- JWT
- OAuth2
- AWS S3
- SSE

---

## 주요 기능

### 프로젝트 관리

- 프로젝트 → 카테고리 → Task 구조 관리
- 예상 작업 시간 설정
- 타이머 기반 실제 작업 시간 기록

### 데이터 분석

- Chart.js 기반 작업 통계 대시보드
- 오버워킹 패턴 분석

### 인증 및 사용자 관리

- OAuth2 소셜 로그인
- JWT 인증
- Access/Refresh Token 구조

### 기타 기능

- SSE 실시간 알림
- AWS S3 Pre-signed URL 이미지 업로드
- next-intl 기반 다국어 지원

---

## 아키텍처

### 도메인 기반 구조

기능 추가가 늘어나면서 코드 결합도가 높아지고 유지보수가 어려워지는 문제가 발생했습니다.

이를 해결하기 위해 도메인 기반 구조로 리팩토링했습니다.

```bash
src
 ┣ domains
 ┃ ┣ dashboard
 ┃ ┣ project
 ┃ ┗ reports
 ┣ shared
 ┃ ┣ components
 ┃ ┣ hooks
 ┃ ┣ api
 ┃ ┗ utils
````

### 도메인 구조

```bash
도메인명/
├── api/                 # 도메인 API
├── components/          # 도메인 UI 컴포넌트
│   ├── ui/              # 도메인 UI 컴포넌트
├── hooks/               # 도메인 커스텀 훅
└── model/
    ├── types.ts         # 도메인 타입 정의
    └── utils.ts         # 유틸 함수
```

### 적용 효과

* 관심사 분리
* 코드 리뷰 범위 축소
* 기능 확장 용이
* 유지보수성 향상

---

## 기술적 개선

### 코드 컨벤션 표준화

Prettier + ESLint 규칙을 정비하여 코드 스타일을 통일했습니다.

결과:

* Git 충돌 발생률 약 90% 감소
* PR 리뷰 시간 평균 30% 단축

---

### 공통 API 모듈 구축

Axios interceptor 기반 API 모듈 구성

* 인증 처리 통합
* 공통 에러 핸들링
* 중복 코드 제거

---

### 데이터 캐싱 최적화

TanStack Query의 Query Key를 도메인 단위로 설계

* staleTime 전략
* invalidation 관리
* 서버 요청 감소

---

## 내가 기여한 부분

* 프론트엔드 리더 역할 수행
* 프로젝트 구조 설계
* 도메인 기반 아키텍처 리팩토링
* 협업 컨벤션 구축
* 공통 API 구조 설계
* 데이터 캐싱 전략 설계
* 실시간 알림 및 다국어 기능 구현

---

## 회고

이번 프로젝트에서는 단순 기능 구현보다
구조 설계와 협업 환경 구축이 장기적인 개발 생산성에 큰 영향을 준다는 점을 체감했습니다.

특히 초기 설계 단계에서 상태 관리 전략, 공통 모듈화, 협업 규칙을 명확히 정의하는 것이 중요하다는 경험을 얻었습니다.

앞으로는 기능 구현보다 문제를 예방하는 구조 설계를 우선하는 개발 방식을 지향하고 있습니다.
