# POMA - 1학기 캡스톤 디자인

[https://dlpoma.store](https://dlpoma.store)

## 소개
POMA는 다양한 종목의 스포츠를 편리하게 즐길 수 있는 플랫폼입니다.  
구장 예약과 매칭 기능을 통해 사용자들이 쉽고 간편하게 스포츠를 즐길 수 있도록 도와줍니다.

## 팀원
총 8명으로 구성된 팀입니다.  
저는 백엔드 개발과 전체 프로젝트 관리, 그리고 프론트엔드 레이아웃 설계 및 기능 구현을 맡았습니다.

- 백엔드 역할
  - 마이페이지 기능 구현 (예약 이력, 매치 이력, 유저 정보 관리 등)
  - 결제 시스템 설계 및 구현 (캐시 충전, 예약 시 캐시 차감, 포트원 API 연동)
- 프론트엔드 역할
  - 전체적인 레이아웃 구조 초안 설계
  - 각 페이지별 기능 제작 및 적용

## 개발 기간
2024-03-19 ~ 2024-09-10

## 기술 스택
- Backend: Spring Boot 3, Spring Security 6, JPA, Gradle  
- Frontend: Thymeleaf, Bootstrap, JavaScript  
- Infra: AWS (RDS, Route53), Let's Encrypt  

## 설계 및 기능 소개

### 보안
- SecurityFilterChain을 통한 기본 보안 설정
- CSRF 토큰 적용

### 화면 설계
- Spring MVC + Thymeleaf 기반 SSR
- 일부 POST 요청은 fetch API를 사용해 UX 개선
- RESTful URL 설계

### 디자인
- Bootstrap을 활용한 반응형 웹 디자인

### DB 설계
- MySQL(RDS) + JPA
- 주요 테이블 관계 예시:
  - 구장(1) - 예약(N) - 매치(1)
  - 팀(1) - 유저(N)
  - 매치(1) - 매치 팀원(N)
  - 리뷰(N) - 유저(1)
  - 게시판(1) - 댓글(N), 부모 댓글(1) - 자식 댓글(N) (Self Join)

## 주요 기능

### 회원가입 & 로그인
- Bcrypt로 비밀번호 해싱
- 분실 계정 찾기: Google SMTP API로 임시 비밀번호 전송

### 구장 예약
- 예약 시 포트원 API를 통한 캐시 결제
