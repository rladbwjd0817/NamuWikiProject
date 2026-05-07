# 🌿 나무위키 — IoT 스마트팜 연동 식물 커뮤니티 플랫폼

> 농장주와 일반 사용자를 잇는 **SNS형 식물 커뮤니티** 웹 플랫폼
> IoT 디바이스로 수집된 실시간 센서 데이터를 시각화하고, 신뢰 기반의 농산물 정보를 공유합니다.

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/SpringBoot_3-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![OpenAI](https://img.shields.io/badge/GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)

---

## 📁 레파지토리 구성

| 레파지토리 | 역할 | 기술 스택 |
|---|---|---|
| [namuwiki](https://github.com/rladbwjd0817/namuwiki) | 백엔드 API 서버 | Java 17, Spring Boot 3, MariaDB, MyBatis, JWT |
| [namuwiki-frontend](https://github.com/rladbwjd0817/namuwiki-frontend) | 웹 프론트엔드 | React 19, TypeScript, TailwindCSS, React Query |

---

## 🛠️ 기술 스택

### App (Backend)
- **Java 17 / Spring Boot 3** — REST API 서버
- **MariaDB / MyBatis** — 관계형 데이터베이스 및 SQL 매핑
- **Spring Security / JWT** — 인증 및 권한 관리
- **SSE (Server-Sent Events)** — AI 챗봇 스트리밍 응답
- **STOMP WebSocket** — 실시간 DM 채팅
- **Swagger (SpringDoc)** — API 문서 자동화

### Web (Frontend)
- **React 19 + TypeScript** — 웹 클라이언트
- **TailwindCSS / shadcn/ui** — 유틸리티 기반 스타일링 & UI 컴포넌트
- **React Query (TanStack Query)** — 서버 상태 관리 & 캐싱
- **Tiptap** — 리치 텍스트 에디터 (이미지, 마크다운 지원)
- **Recharts** — 센서 히스토리 차트 시각화
- **i18n** — 다국어 지원
- **next-themes** — 다크모드 지원

### 외부 API
- **PlantNet** — AI 딥러닝 기반 식물 사진 식별
- **산림청 KPNI (국가표준식물목록)** — 식물 한국어 학명 정보 조회
- **OpenAI GPT-4.1** — 식물 전문 AI 챗봇

### 인프라 / DevOps
- **AWS EC2** — 서버 배포
- **AWS RDS (MariaDB)** — 클라우드 데이터베이스
- **AWS S3** — 이미지 스토리지 (Presigned URL)
- **GitHub Actions** — CI/CD 자동 배포

---

## ✨ 주요 기능

---

### 🌐 Web (웹 플랫폼 — React 19)

#### 🔐 회원 인증 & 역할 권한 관리
- 이메일 기반 회원가입 / 로그인
- **역할 3단계 분리** : 일반 유저 / 농장주 / 관리자
- 농장주 가입 시 관리자 발급 **인증번호 검증** 후 권한 부여
- 역할별 사이드바 및 메뉴 **조건부 렌더링**으로 맞춤 기능 접근성 제공
- 본인 게시글만 수정/삭제 가능한 **UI 레벨 권한 관리**

#### 📰 SNS형 메인피드 & 커뮤니티
- 회원들의 게시글을 SNS 형태로 노출하는 **메인피드**
- **Tiptap 리치 에디터** 기반 이미지 포함 게시글 CRUD
- 게시글 작성자 역할 **뱃지** 표시 (농장주 / 일반 유저 구분)
- 댓글 등록 / 수정 / 삭제 + **좋아요** 기능
- 팔로우한 농장주 · 유저 소식 **실시간 반영**

#### 👥 팔로우 & 소셜 기능
- 팔로우 / 팔로워 목록 조회
- 관심 농장주 구독으로 신뢰 기반 정보 수신

#### 💬 DM (실시간 1:1 채팅)
- **STOMP WebSocket** 기반 다이렉트 메시지
- 채팅 목록 및 채팅방 UI

#### 🤖 AI 식물 식별 & 챗봇
- 사진 업로드 → **PlantNet AI**가 식물 학명, 속명, 과명, 유사도 점수 반환
- **산림청 KPNI API** 연동으로 학명을 한국어 이름으로 자동 매핑, 상위 3개 후보 표시
- **GPT-4.1** 기반 식물 전문가 챗봇, **SSE 스트리밍**으로 실시간 타이핑 효과 출력

#### 👤 마이페이지
- 프로필 사진 변경 (AWS S3 업로드)
- 내 게시글 · 댓글 활동 기록 조회
- 개인정보 수정

---

### ⚙️ App (스마트팜 IoT 연동 — Spring Boot 3)

#### 🏡 농장 · 농작물 관리 (농장주)
- 농장 등록 (이름, 주소, 소개) / 목록 및 상세 조회
- 농작물 등록 (작물명, 설명, 가격) — 등록 즉시 조회 가능
- 일반 유저: **전체 농장 목록 검색** + 팔로우 기능

#### 📡 IoT 기기 · 실시간 센서 데이터
- IoT 디바이스 등록 / 활성화 관리
- **최신 센서 데이터** — 10초마다 자동 갱신 (폴링 방식, 구현 복잡도 최소화)
  - 온도 · 습도 · 토양수분 · 조도(LDR) 측정값
  - 팬 · LED · 펌프 **구동기 상태** 표시
- **히스토리 센서 차트** (Recharts AreaChart)
  - 기간 선택 → startDate 자동 계산 → 60초마다 자동 갱신
  - 기간별 시간 포맷 다르게 적용 (UX 고려)
  - 데이터 1건 이하 시 안내 문구 표시
- 센서 측정값과 **임계값 비교** → **생육상태 뱃지** 출력 (농장주 신뢰도 제공)
- 일반 유저 / 농장주 **동일 컴포넌트 재사용** (`isFarmOwner` 분기 처리)

#### 🛠️ 관리자 기능
- 전체 회원 조회 · **권한 변경** (일반유저 ↔ 농장주)
- **관리자 계정 추가** (관리자 영역에서만 가능, 남용 방지)
- **농장주 인증번호 생성** 및 발급
- 전체 게시글 · 댓글 관리 (수정, 삭제) — 표 형식으로 한눈에 비교·필터링

#### 🔑 보안 · 인프라 (Backend)
- **Spring Security + JWT** 인증 및 역할 권한 관리 (stateless)
- **AWS S3 Presigned URL** 로 안전한 파일 업로드/접근
- **GitHub Actions** 기반 CI/CD 자동 배포
- Controller → Service → Mapper **레이어드 아키텍처**
- JOIN + IS_ACTIVE 필터 + LIMIT 1 로 **불필요한 데이터 조회 최소화**

---

## 🗂️ ERD

![ERD](https://mermaid.ink/img/ZXJEaWFncmFtCiAgICBNRU1CRVIgewogICAgICAgIHZhcmNoYXIgbWVtX2VtYWlsIFBLCiAgICAgICAgdmFyY2hhciBtZW1fcHcKICAgICAgICB2YXJjaGFyIG1lbV9yb2xlCiAgICAgICAgdmFyY2hhciBtZW1fbmlja25hbWUKICAgICAgICB2YXJjaGFyIG1lbV9uYW1lCiAgICAgICAgdmFyY2hhciBtZW1fdGVsCiAgICAgICAgdmFyY2hhciBtZW1fYWRkCiAgICAgICAgdmFyY2hhciBhZGRfZGV0YWlsCiAgICAgICAgdmFyY2hhciBtZW1fcHJvZmlsZV9pbWcKICAgICAgICB2YXJjaGFyIGZhcm1lcl9uYW1lCiAgICAgICAgdmFyY2hhciBhdXRoX2NvZGUKICAgICAgICBkYXRldGltZSBtZW1fam9pbl9kYXRlCiAgICB9CiAgICBGQVJNIHsKICAgICAgICBiaWdpbnQgZmFybV9pZCBQSwogICAgICAgIHZhcmNoYXIgZmFybWVyX2VtYWlsIEZLCiAgICAgICAgdmFyY2hhciBmYXJtX25hbWUKICAgICAgICB2YXJjaGFyIGZhcm1fYWRkCiAgICAgICAgZGF0ZXRpbWUgY3JlYXRlZF9hdAogICAgfQogICAgQ1JPUCB7CiAgICAgICAgYmlnaW50IGNyb3BfaWQgUEsKICAgICAgICBiaWdpbnQgZmFybV9pZCBGSwogICAgICAgIHZhcmNoYXIgY3JvcF9uYW1lCiAgICAgICAgdmFyY2hhciBjcm9wX2Rlc2MKICAgICAgICBpbnQgY3JvcF9wcmljZQogICAgfQogICAgREVWSUNFIHsKICAgICAgICB2YXJjaGFyIGRldmljZV9pZCBQSwogICAgICAgIGJpZ2ludCBjcm9wX2lkIEZLCiAgICAgICAgdmFyY2hhciBmYXJtZXJfZW1haWwgRksKICAgICAgICB0aW55aW50IGlzX2FjdGl2ZQogICAgICAgIGRhdGV0aW1lIHJlZ2lzdGVyZWRfYXQKICAgICAgICBkYXRldGltZSBjcmVhdGVkX2F0CiAgICB9CiAgICBTRU5TT1JfREFUQSB7CiAgICAgICAgYmlnaW50IGlkIFBLCiAgICAgICAgdmFyY2hhciBkZXZpY2VfaWQgRksKICAgICAgICBmbG9hdCB0ZW1wX2MKICAgICAgICBmbG9hdCBodW1pZGl0eQogICAgICAgIGludCBzb2lsX21vaXN0dXJlX3ZhbHVlCiAgICAgICAgaW50IGxkcl92YWx1ZQogICAgICAgIHRpbnlpbnQgZmFuX3N0YXR1cwogICAgICAgIHRpbnlpbnQgbGVkX3N0YXR1cwogICAgICAgIHRpbnlpbnQgcHVtcF9zdGF0dXMKICAgICAgICBmbG9hdCB0ZW1wX21pbgogICAgICAgIGZsb2F0IHRlbXBfbWF4CiAgICAgICAgaW50IHNvaWxfbWluCiAgICAgICAgaW50IHNvaWxfbWF4CiAgICAgICAgaW50IGx1eF9taW4KICAgICAgICBpbnQgbHV4X21heAogICAgICAgIGRhdGV0aW1lIGNyZWF0ZV9kYXRlCiAgICB9CiAgICBQT1NUIHsKICAgICAgICBiaWdpbnQgcG9zdF9pZCBQSwogICAgICAgIHZhcmNoYXIgbWVtX2VtYWlsIEZLCiAgICAgICAgdmFyY2hhciBwb3N0X2ltZwogICAgICAgIHZhcmNoYXIgdGl0bGUKICAgICAgICB0ZXh0IGNvbnRlbnQKICAgICAgICBpbnQgdmlld19jb3VudAogICAgICAgIGludCBsaWtlX2NvdW50CiAgICAgICAgaW50IGNvbW1lbnRfY291bnQKICAgICAgICBkYXRldGltZSBjcmVhdGVkX2F0CiAgICAgICAgZGF0ZXRpbWUgdXBkYXRlZF9hdAogICAgfQogICAgQ09NTUVOVCB7CiAgICAgICAgYmlnaW50IGNvbW1lbnRfaWQgUEsKICAgICAgICBiaWdpbnQgcG9zdF9pZCBGSwogICAgICAgIHZhcmNoYXIgbWVtX2VtYWlsIEZLCiAgICAgICAgdGV4dCBjb250ZW50CiAgICAgICAgZGF0ZXRpbWUgY3JlYXRlZF9hdAogICAgfQogICAgUE9TVF9MSUtFIHsKICAgICAgICBiaWdpbnQgbGlrZV9pZCBQSwogICAgICAgIGJpZ2ludCBwb3N0X2lkIEZLCiAgICAgICAgdmFyY2hhciBtZW1fZW1haWwgRksKICAgICAgICBkYXRldGltZSBjcmVhdGVkX2F0CiAgICB9CiAgICBGT0xMT1cgewogICAgICAgIGJpZ2ludCBmb2xsb3dfaWQgUEsKICAgICAgICB2YXJjaGFyIGZvbGxvd2VyX2VtYWlsIEZLCiAgICAgICAgdmFyY2hhciBmb2xsb3dpbmdfZW1haWwgRksKICAgICAgICBkYXRldGltZSBjcmVhdGVkX2F0CiAgICB9CiAgICBETSB7CiAgICAgICAgYmlnaW50IGRtX2lkIFBLCiAgICAgICAgdmFyY2hhciBzZW5kZXJfZW1haWwgRksKICAgICAgICB2YXJjaGFyIHJlY2VpdmVyX2VtYWlsIEZLCiAgICAgICAgdGV4dCBjb250ZW50CiAgICAgICAgZGF0ZXRpbWUgc2VudF9hdAogICAgfQogICAgTUVNQkVSIHx8LS1veyBGQVJNIDogb3ducwogICAgRkFSTSB8fC0tb3sgQ1JPUCA6IGhhcwogICAgQ1JPUCB8fC0tb3wgREVWSUNFIDogY29ubmVjdHMKICAgIERFVklDRSB8fC0tb3sgU0VOU09SX0RBVEEgOiBjb2xsZWN0cwogICAgTUVNQkVSIHx8LS1veyBQT1NUIDogd3JpdGVzCiAgICBQT1NUIHx8LS1veyBDT01NRU5UIDogaGFzCiAgICBQT1NUIHx8LS1veyBQT1NUX0xJS0UgOiByZWNlaXZlcwogICAgTUVNQkVSIHx8LS1veyBGT0xMT1cgOiBmb2xsb3dzCiAgICBNRU1CRVIgfHwtLW97IERNIDogc2VuZHM=)

---

## 🎬 시연 영상 / 스크린샷

---

### 🌐 Web — 공통 기능

#### 회원가입 & 로그인 (JWT 인증)

| 회원가입 (역할 선택) | 로그인 |
|---|---|
| 📷 스크린샷 삽입 예정 | 📷 스크린샷 삽입 예정 |

---

#### 메인피드 (SNS형 피드)

| 일반 유저 피드 | 농장주 피드 |
|---|---|
| 📷 스크린샷 삽입 예정 | 📷 스크린샷 삽입 예정 |

---

#### 피드 상세 페이지 — 댓글 · 좋아요 (시연 영상)

<!-- 🎥 시연 영상 삽입 자리 : 피드 상세 페이지 (댓글 등록/수정/삭제, 좋아요, 팔로우) -->
🎥 **[ 시연 영상 삽입 예정 ]**

---

#### 마이페이지 — 프로필 수정 (시연 영상)

<!-- 🎥 시연 영상 삽입 자리 : 마이페이지 프로필 사진 수정 (S3 업로드), 내 활동 기록 -->
🎥 **[ 시연 영상 삽입 예정 ]**

---

### ⚙️ App — 일반 유저 기능

#### 농장 목록 · 검색 · 팔로우

<!-- 📷 스크린샷 삽입 자리 : 일반 유저 전체 농장 목록, 검색, 팔로우, 상세 조회 -->
📷 **[ 스크린샷 삽입 예정 ]**

---

#### 농작물 센서 데이터 조회 (최신값 + 히스토리 차트)

<!-- 📷 스크린샷 삽입 자리 : 센서 최신값, 히스토리 AreaChart, 생육상태 뱃지 -->
📷 **[ 스크린샷 삽입 예정 ]**

---

### ⚙️ App — 농장주 기능

#### 내 농장 관리 페이지 (농장 · 농작물 등록)

<!-- 📷 스크린샷 삽입 자리 : 농장 등록, 농작물 추가, 나의 농장 목록 -->
📷 **[ 스크린샷 삽입 예정 ]**

---

#### 기기 관리 페이지 (IoT 디바이스 등록 · 목록)

<!-- 📷 스크린샷 삽입 자리 : IoT 기기 등록, 목록, 활성화 관리 -->
📷 **[ 스크린샷 삽입 예정 ]**

---

#### 나의 농장 목록 — 센서 데이터 모니터링

<!-- 📷 스크린샷 삽입 자리 : 농장주 센서 데이터 대시보드 (isFarmOwner 분기) -->
📷 **[ 스크린샷 삽입 예정 ]**

---

### 🛠️ App — 관리자 기능

#### 회원 관리 — 관리자 추가 · 권한 변경 (시연 영상)

<!-- 🎥 시연 영상 삽입 자리 : 관리자 추가 모달 + 회원 권한 변경 모달 -->
🎥 **[ 시연 영상 삽입 예정 ]**

---

#### 게시글 관리 (시연 영상)

<!-- 🎥 시연 영상 삽입 자리 : 전체 게시글/댓글 관리, 수정/삭제 -->
🎥 **[ 시연 영상 삽입 예정 ]**

---

## 🗓️ 개발 기간 & 타임라인

| 단계 | 기간 | 내용 |
|------|------|------|
| 1. 기획 · 설계 | 4월 6일 | 요구사항 정의, Figma 화면 설계, API 명세서 작성, DB 테이블 설계 |
| 2. 핵심 기능 개발 | 4월 7일 ~ 4월 9일 | 회원가입/로그인, JWT 인증, 게시글 CRUD, 농장 등록/조회 |
| 3. 고급 기능 구현 | 4월 10일 ~ 4월 15일 | 팔로우/팔로워, 관리자 페이지, AWS S3 연동, 농장주/일반 유저 페이지 |
| 4. 통합 · 마무리 | 4월 16일 | 프론트-백엔드 통합, UI 디자인 완성, 버그 수정, 발표 준비 |

---

## 📂 프로젝트 구조

```
namuwiki/                          # 백엔드
├── global/
│   ├── config/                    # CORS, Swagger, WebClient, AWS S3 설정
│   └── exception/                 # 전역 예외 처리
├── security/
│   └── jwt/                       # JWT 필터
├── member/                        # 회원 도메인
├── plant/                         # 식물 식별 (PlantNet + KPNI)
├── openai/                        # GPT-4.1 스트리밍 챗봇
└── util/                          # 파일 유틸

namuwiki-frontend/                 # 프론트엔드
└── src/
    ├── api/                       # API 호출 모듈
    ├── components/                # 공통 UI 컴포넌트
    ├── queries/                   # React Query 훅
    ├── routes/pages/              # 페이지 컴포넌트 (역할별 분리)
    ├── types/                     # TypeScript 타입 정의
    └── utils/                     # Axios 인터셉터, 유틸
```

---

## 🚀 실행 방법

### Backend
```bash
# src/main/resources/application-dev.properties 생성 후 환경변수 설정
./gradlew bootRun
```

### Frontend
```bash
npm install
npm run dev
```

---

## 🤝 협업 방식

- **GitHub 브랜치 전략** : `main → dev → feature` 브랜치 단위 개발, PR 리뷰 후 병합
- **풀스택 방식** : 기능 단위 역할 분담, 슬랙 + 대면 진행 상황 공유
- **API 명세서 선작성** : 프론트-백엔드 동시 개발을 위해 도메인별 엔드포인트, 요청/응답, 인증 여부 사전 정의

---

## 👥 팀 구성

| 이름 | 역할 |
|------|------|
| 황민서 | Frontend / Backend |
| 김재근 | Frontend / Backend |
| 김유정 | Frontend / Backend |

---

<div align="center">
  <sub>2026 나무위키 | Built with 🌿</sub>
</div>
