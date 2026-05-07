# 🌿 나무위키 — IoT 스마트팜 연동 식물 커뮤니티 플랫폼

> 농장주와 일반 사용자를 잇는 **SNS형 식물 커뮤니티** 플랫폼
> IoT 디바이스로 수집된 실시간 센서 데이터를 시각화하고, 신뢰 기반의 농산물 정보를 공유합니다.

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/SpringBoot_3-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)

---

## 📁 레파지토리 구성

| 레파지토리 | 역할 | 기술 스택 |
|---|---|---|
| [namuwiki](https://github.com/rladbwjd0817/namuwiki) | 백엔드 API 서버 | Java 17, Spring Boot 3, MariaDB, MyBatis, JWT |
| [namuwiki-frontend](https://github.com/rladbwjd0817/namuwiki-frontend) | 웹 프론트엔드 | React 19, TypeScript, TailwindCSS, React Query |
| [namuwiki-app](https://github.com/james14kr/namuwiki-app) | 모바일 앱 | React Native, Expo 54, TypeScript, TanStack Query |

---

## 🛠️ 기술 스택

### Backend
- **Java 17 / Spring Boot 3** — REST API 서버
- **MariaDB / MyBatis** — 관계형 데이터베이스 및 SQL 매핑
- **Spring Security / JWT** — 인증 및 권한 관리
- **SSE (Server-Sent Events)** — 실시간 알림 스트리밍
- **STOMP WebSocket** — 실시간 DM 채팅
- **Swagger (SpringDoc)** — API 문서 자동화

### Web (Frontend)
- **React 19 + TypeScript** — 웹 클라이언트
- **TailwindCSS / shadcn/ui** — 유틸리티 기반 스타일링 & UI 컴포넌트
- **React Query (TanStack Query)** — 서버 상태 관리 & 캐싱
- **Tiptap** — 리치 텍스트 에디터 (이미지, 마크다운 지원)
- **Recharts** — 센서 히스토리 차트 시각화
- **next-themes** — 다크모드 지원

### App (Mobile — React Native + Expo)
- **React Native 0.81 / Expo 54 / TypeScript** — 크로스플랫폼 모바일 앱 (Android / iOS)
- **Expo Router** — 파일 기반 화면 라우팅
- **TanStack Query** — 서버 상태 관리 & 캐싱
- **Axios** — HTTP 클라이언트
- **STOMP WebSocket + SockJS** — 실시간 DM 채팅
- **SSE (react-native-sse)** — 팔로우 / 댓글 실시간 인앱 알림
- **expo-secure-store** — JWT 토큰 안전 저장
- **Zod** — 입력 유효성 검증
- **react-native-gifted-charts** — 센서 히스토리 차트 시각화
- **expo-location** — 위치 기반 날씨 조회
- **expo-image-picker / expo-image-manipulator** — 이미지 선택 및 처리
- **react-native-daum-postcode** — 주소 검색

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

#### 📡 농장 & IoT 센서 모니터링
- 전체 농장 목록 검색 및 상세 조회
- 센서 데이터(온도 · 습도 · 토양수분 · 조도) **10초마다 자동 갱신** (폴링 방식)
- **Recharts AreaChart** 기반 히스토리 차트 시각화
- 센서 임계값 비교 → **생육상태 뱃지** 출력

#### 👤 마이페이지
- 프로필 사진 변경 (AWS S3 업로드)
- 내 게시글 · 댓글 활동 기록 조회
- 개인정보 수정

#### 🛠️ 관리자 기능
- 전체 회원 조회 · **권한 변경** (일반유저 ↔ 농장주)
- **관리자 계정 추가** (관리자 영역에서만 가능, 남용 방지)
- **농장주 인증번호 생성** 및 발급
- 전체 게시글 · 댓글 관리 (수정, 삭제) — 표 형식으로 한눈에 비교·필터링

---

### 📱 App (모바일 앱 — React Native + Expo)

#### 🔐 인증
- 이메일 기반 로그인 / 회원가입
- JWT 토큰 expo-secure-store 저장, 역할(농장주 / 일반 유저)에 따라 전용 탭 화면으로 자동 분기

#### 🌾 농장주 화면
- **홈** : 내 농장 목록 빠른 접근
- **농장 관리** : 농장 등록/삭제 (다음 주소 검색 연동), 작물 등록/삭제
- **IoT 디바이스** : 디바이스 등록 · 활성화, 작물 연결/해제, 전체 기기 목록 관리
- **실시간 센서 조회** : 온도 · 습도 · 토양수분 · 조도, 팬 · LED · 펌프 상태 표시
- **센서 히스토리 차트** (react-native-gifted-charts) : 기간 선택 후 시계열 데이터 시각화
- **임계값 설정** : 센서 이상 감지 기준값 변경
- **기기 원격 제어** : 팬 · LED · 펌프 ON/OFF

#### 👤 일반 사용자 화면
- **홈** : expo-location 현재 위치 기반 날씨 배너 표시 (맑음 / 비 / 눈 / 흐림 배경 이미지)
- **농장 탐색** : 전체 농장 목록 검색 및 상세 조회
- **작물 건강 상태** : 작물별 센서 데이터 기반 건강 현황 조회

#### 📰 SNS 피드 (공통 — 웹과 동일 기능, 모바일 화면)
- 게시글 목록 / 상세 조회, 작성 / 수정 / 삭제
- 댓글 등록 / 수정 / 삭제 + 좋아요
- 게시글 작성자 역할 뱃지 표시 (농장주 / 일반 유저)

#### 👥 팔로우 & 알림 (공통 — 웹과 동일 기능, 모바일 화면)
- 농장주 / 유저 팔로우 / 언팔로우
- SSE 기반 실시간 인앱 알림 (팔로우 · 댓글 이벤트)
- NotificationContext 전역 상태 관리

#### 💬 DM 채팅 (공통 — 웹과 동일 기능, 모바일 화면)
- STOMP WebSocket + SockJS 기반 실시간 1:1 채팅
- DM 목록 → 채팅방 화면

#### 🙍 마이페이지 (공통 — 웹과 동일 기능, 모바일 화면)
- 프로필 이미지 변경 (expo-image-picker)
- 개인정보 수정

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

🎥 **[ 시연 영상 삽입 예정 ]**

---

#### 마이페이지 — 프로필 수정 (시연 영상)

🎥 **[ 시연 영상 삽입 예정 ]**

---

### 📱 App — 일반 사용자 기능

#### 홈 화면 날씨 배너 / 농장 탐색 / 팔로우

📷 **[ 스크린샷 삽입 예정 ]**

---

#### 작물 건강 상태 조회 (센서 데이터)

📷 **[ 스크린샷 삽입 예정 ]**

---

#### SNS 피드 / 댓글 / 좋아요

📷 **[ 스크린샷 삽입 예정 ]**

---

#### DM 채팅 / 실시간 알림

📷 **[ 스크린샷 삽입 예정 ]**

---

### 📱 App — 농장주 기능

#### 내 농장 관리 (농장 · 작물 등록)

📷 **[ 스크린샷 삽입 예정 ]**

---

#### 기기 관리 (IoT 디바이스 등록 · 연결)

📷 **[ 스크린샷 삽입 예정 ]**

---

#### 센서 데이터 모니터링 + 히스토리 차트

📷 **[ 스크린샷 삽입 예정 ]**

---

#### 기기 원격 제어

📷 **[ 스크린샷 삽입 예정 ]**

---

### 🛠️ App — 관리자 기능

#### 회원 관리 — 관리자 추가 · 권한 변경 (시연 영상)

🎥 **[ 시연 영상 삽입 예정 ]**

---

#### 게시글 관리 (시연 영상)

🎥 **[ 시연 영상 삽입 예정 ]**

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
└── util/                          # 파일 유틸

namuwiki-frontend/                 # 웹 프론트엔드
└── src/
    ├── api/                       # API 호출 모듈
    ├── components/                # 공통 UI 컴포넌트
    ├── queries/                   # React Query 훅
    ├── routes/pages/              # 페이지 컴포넌트 (역할별 분리)
    ├── types/                     # TypeScript 타입 정의
    └── utils/                     # Axios 인터셉터, 유틸

namuwiki-app/                      # 모바일 앱 (React Native + Expo)
├── app/
│   ├── (auth)/                    # 로그인, 회원가입
│   ├── (farmer-tabs)/             # 농장주 탭 네비게이션
│   │   ├── index.tsx              # 홈
│   │   ├── device.tsx             # 디바이스 관리
│   │   ├── dm.tsx                 # DM 목록
│   │   ├── profile.tsx            # 프로필
│   │   └── farm/                  # 농장 · 작물 · 센서 · 기기 제어
│   │       ├── index.tsx          # 내 농장 목록
│   │       ├── [farmId].tsx       # 농장 상세
│   │       ├── register.tsx       # 농장 등록
│   │       ├── cropRegister.tsx   # 작물 등록
│   │       ├── sensor.tsx         # 센서 데이터 조회
│   │       └── control.tsx        # 기기 원격 제어
│   ├── (user-tabs)/               # 일반 사용자 탭 네비게이션
│   │   ├── index.tsx              # 홈 (날씨 배너)
│   │   ├── dm.tsx                 # DM 목록
│   │   ├── profile.tsx            # 프로필
│   │   └── farm/                  # 농장 탐색
│   │       ├── index.tsx          # 전체 농장 목록
│   │       ├── [farmId].tsx       # 농장 상세
│   │       └── cropHealth/[cropId].tsx  # 작물 건강 상태
│   ├── dm/[roomId].tsx            # DM 채팅방
│   └── post/                      # SNS 피드 (목록 · 상세 · 작성 · 수정)
├── api/                           # Axios 기반 API 호출 모듈
├── queries/                       # TanStack Query 훅 (도메인별 분리)
│   ├── crop/                      # 작물 CRUD
│   ├── device/                    # 디바이스 관리
│   ├── farm/                      # 농장 관리
│   └── sensor/                    # 센서 데이터 조회
├── components/                    # 공통 UI 컴포넌트
├── contexts/                      # 전역 컨텍스트 (알림)
├── hooks/                         # 커스텀 훅 (채팅, 알림)
└── constants/                     # 테마 상수
```

---

## 🚀 실행 방법

### Backend
```bash
# src/main/resources/application-dev.properties 생성 후 환경변수 설정
./gradlew bootRun
```

### Frontend (Web)
```bash
npm install
npm run dev
```

### App (Mobile)
```bash
npm install
npx expo start
```

---

## 🤝 협업

### 협업 방식

- **GitHub 브랜치 전략** : `main → dev → feature` 브랜치 단위 개발, PR 리뷰 후 병합
- **풀스택 방식** : 기능 단위 역할 분담, Slack + 대면 진행 상황 공유
- **Figma 화면 설계 선작업** : 웹 / 모바일 화면 흐름을 개발 전 사전 정의해 개발 방향 통일
- **API 명세서 선작성** : 프론트 · 앱 · 백엔드 동시 개발을 위해 도메인별 엔드포인트, 요청/응답, 인증 여부 사전 정의

---

### Figma — 화면 설계

웹 / 모바일 화면 흐름을 개발 전 사전 정의해 개발 방향 통일

| 웹 화면 설계 | 모바일 화면 설계 |
|---|---|
| 📷 스크린샷 삽입 예정 | 📷 스크린샷 삽입 예정 |

---

### API 명세서 — 프론트 / 앱 동시 개발을 위한 사전 작성

도메인별 엔드포인트, 요청/응답 형식, 인증 여부를 사전 정의해 프론트엔드 · 앱 · 백엔드 동시 개발 진행

| API 명세서 전체 |
|------|
| <img width="446" height="545" alt="API 명세서" src="https://github.com/user-attachments/assets/2c56ec15-6646-483f-928e-dd6cbc1b1d5c" />|

---

### Slack — 팀 커뮤니케이션

일정 공유, 이슈 논의, 진행 상황 공유 등 팀 전체 소통 채널로 활용

| Slack 채널 및 이슈 / 진행 공유 |
|------|
| <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/54845634-dd19-46ba-9ba7-ae1e2b5fc311" />
 | <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/6cf7cace-7c0c-4460-9017-ca7ec9e63769" />|

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
