# 🌿 나무위키 — AI 식물 식별 & 스마트 농장 관리 플랫폼

> 사진 한 장으로 식물을 식별하고, IoT 센서로 농장을 실시간 관리하며,  
> 농업인과 소비자가 함께하는 식물 커뮤니티 플랫폼입니다.

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/SpringBoot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![OpenAI](https://img.shields.io/badge/GPT--4.1-412991?style=flat-square&logo=openai&logoColor=white)

---

## 📁 레파지토리 구성

| 레파지토리 | 역할 | 기술 스택 |
|---|---|---|
| [namuwiki](https://github.com/본인레파지토리/namuwiki) | 백엔드 API 서버 | Java 17, Spring Boot, MariaDB, MyBatis, JWT |
| [namuwiki-frontend](https://github.com/본인레파지토리/namuwiki-frontend) | 웹 프론트엔드 | React, TypeScript, TailwindCSS, React Query |

---

## 🎬 시연 영상 / 스크린샷

> **[ GIF 또는 시연 영상 삽입 예정 ]**

| 식물 AI 식별 | 센서 모니터링 | 커뮤니티 피드 |
|---|---|---|
| 📷 삽입 예정 | 📷 삽입 예정 | 📷 삽입 예정 |

---

## 🛠️ 기술 스택

### Backend
- **Java 17 / Spring Boot** — REST API 서버
- **MariaDB / MyBatis** — 관계형 데이터베이스 및 SQL 매핑
- **Spring Security / JWT** — 인증 및 권한 관리
- **SSE (Server-Sent Events)** — AI 챗봇 스트리밍 응답
- **Swagger (SpringDoc)** — API 문서 자동화

### Frontend
- **React + TypeScript** — 웹 클라이언트
- **TailwindCSS** — 유틸리티 기반 스타일링
- **React Query (TanStack Query)** — 서버 상태 관리
- **Tiptap** — 리치 텍스트 에디터 (마크다운 지원)
- **Storybook** — UI 컴포넌트 독립 개발 및 문서화
- **i18n** — 다국어 지원

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

### 🌿 AI 식물 식별
- 사진 업로드 → **PlantNet AI**가 식물 학명, 속명, 과명, 유사도 점수 반환
- **산림청 KPNI API** 연동으로 학명을 한국어 이름으로 자동 매핑
- 상위 3개 후보 결과 동시 표시 및 최적 일치 하이라이트

### 🤖 AI 식물 챗봇
- **GPT-4.1** 기반 식물 전문가 챗봇
- **SSE(Server-Sent Events)** 스트리밍 방식으로 응답을 실시간으로 타이핑 효과 출력
- 식물 외 질문은 자동 차단, 마크다운 형식으로 응답

### 🌾 스마트 농장 관리
- 농장 등록/조회/삭제
- 농장별 작물(이름, 설명, 가격) 등록 및 관리
- IoT 장치를 특정 작물에 연결하여 데이터 수집

### 📊 실시간 센서 모니터링
- **온도·습도·토양수분·조도** 실시간 데이터 조회
- **팬·LED·펌프** 액추에이터 상태 확인
- 센서 히스토리 차트로 시간대별 추이 시각화
- 최솟값/최댓값 기준치 설정 기반 임계값 관리

### 📝 커뮤니티 & 소셜
- **농업인 / 소비자** 역할별 피드 카테고리 분리
- **Tiptap 리치 에디터**로 이미지 포함 게시글 작성
- 좋아요, 댓글, 조회수 기능
- 팔로우 / 언팔로우, 유저 간 **DM(다이렉트 메시지)**

### 🛡️ 권한 관리
- **농업인 / 소비자** 2가지 사용자 역할 구분
- 관리자 전용 IoT 장치 생성 및 전체 장치 관리 대시보드
- JWT 기반 stateless 인증

---

## 📐 ERD

```mermaid
erDiagram
    MEMBER {
        varchar mem_email PK
        varchar mem_pw
        varchar mem_role
        varchar mem_nickname
        varchar mem_name
        varchar mem_tel
        varchar mem_add
        varchar add_detail
        varchar mem_profile_img
        varchar farmer_name
        varchar auth_code
        datetime mem_join_date
    }

    FARM {
        bigint farm_id PK
        varchar farmer_email FK
        varchar farm_name
        varchar farm_add
        datetime created_at
    }

    CROP {
        bigint crop_id PK
        bigint farm_id FK
        varchar crop_name
        varchar crop_desc
        int crop_price
    }

    DEVICE {
        varchar device_id PK
        bigint crop_id FK
        varchar farmer_email FK
        tinyint is_active
        datetime registered_at
        datetime created_at
    }

    SENSOR_DATA {
        bigint id PK
        varchar device_id FK
        float temp_c
        float humidity
        int soil_moisture_value
        int ldr_value
        tinyint fan_status
        tinyint led_status
        tinyint pump_status
        float temp_min
        float temp_max
        int soil_min
        int soil_max
        int lux_min
        int lux_max
        datetime create_date
    }

    POST {
        bigint post_id PK
        varchar mem_email FK
        varchar title
        text content
        int view_count
        int like_count
        int comment_count
        datetime created_at
        datetime updated_at
    }

    COMMENT {
        bigint comment_id PK
        bigint post_id FK
        varchar mem_email FK
        text content
        datetime created_at
    }

    POST_LIKE {
        bigint like_id PK
        bigint post_id FK
        varchar mem_email FK
        datetime created_at
    }

    FOLLOW {
        bigint follow_id PK
        varchar follower_email FK
        varchar following_email FK
        datetime created_at
    }

    DM {
        bigint dm_id PK
        varchar sender_email FK
        varchar receiver_email FK
        text content
        datetime sent_at
    }

    MEMBER ||--o{ FARM : "소유"
    FARM ||--o{ CROP : "보유"
    CROP ||--o| DEVICE : "연결"
    DEVICE ||--o{ SENSOR_DATA : "수집"
    MEMBER ||--o{ POST : "작성"
    POST ||--o{ COMMENT : "포함"
    POST ||--o{ POST_LIKE : "받음"
    MEMBER ||--o{ FOLLOW : "팔로우"
    MEMBER ||--o{ DM : "전송"
