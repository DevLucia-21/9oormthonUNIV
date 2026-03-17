# Spring Boot + JWT + Redis Security Project

Spring Boot 기반의 JWT 인증/인가 학습 프로젝트입니다.

Spring Security 필터 체인, JWT 발급 및 검증, Redis 기반 데이터 저장 기능을 직접 구현하며   
Stateless 인증 구조의 전체 흐름을 학습하는 데 초점을 두었습니다.

---

## Overview

이 프로젝트는 Spring Boot와 Spring Security를 기반으로   
JWT 인증/인가 흐름을 직접 구현해보기 위한 학습용 프로젝트입니다.

단순 로그인 기능 구현을 넘어,

* Spring Security 필터 체인 구성
* JWT 발급 및 검증 로직 구현
* Stateless 인증 방식 이해
* Redis를 활용한 TTL 기반 데이터 저장 실습

까지 직접 다루며 인증 구조 전반을 학습하는 데 목적이 있습니다.

---

## Learning Goals

* JWT 기반 인증/인가 흐름 이해
* Spring Security 필터 체인 구조 학습
* Custom 인증 흐름과 AuthenticationManager 동작 이해
* Redis를 활용한 TTL 저장 방식 실습

---

## Tech Stack

| Category   | Technology                |
| ---------- | ------------------------- |
| Language   | Java 17                   |
| Framework  | Spring Boot 3.4.5         |
| Security   | Spring Security           |
| JWT        | JJWT 0.12.3               |
| Database   | MySQL + Spring Data JPA   |
| Cache      | Redis + Spring Data Redis |
| Build Tool | Gradle                    |
| Library    | Lombok, Jackson Databind  |
| IDE        | IntelliJ IDEA             |

---

## Directory Structure

```text id="jwt1"
jwtsecurity/
├─ src/main/java/com/pye/jwtsecurity/
│  ├─ config/
│  ├─ controller/
│  ├─ dto/
│  ├─ entity/
│  ├─ jwt/
│  ├─ repository/
│  ├─ service/
│  └─ JwtsecurityApplication.java
├─ src/test/java/com/pye/jwtsecurity/
├─ gradle/
├─ libs/
├─ build.gradle
└─ README.md
```

---

## Key Features

### Authentication & Authorization

* `POST /join` : 회원가입 처리
* `POST /login` : 로그인 후 JWT 발급
* `GET /admin` : 관리자 권한 확인용 API
* `JWTFilter`, `LoginFilter`, `JWTUtil`을 직접 구현하여 인증 흐름 구성

### Security Configuration

* `SecurityFilterChain` 기반 커스텀 보안 설정
* 세션 비활성화(`STATELESS`)를 통한 JWT 기반 인증 구조 적용
* `/login`, `/join`, `/`, `/redis/**`는 인증 없이 접근 가능
* `/admin/**`는 `ROLE_ADMIN` 권한 필요

### Redis Integration

* `POST /redis/set` : TTL 기반 데이터 저장
* `GET /redis/get` : Redis 데이터 조회
* `DELETE /redis/delete` : Redis 데이터 삭제

---

## Implementation Details

* 회원가입은 `JoinController`와 `JoinService`를 통해 처리
* 로그인은 기본 formLogin이 아닌 `LoginFilter`로 직접 처리
* 로그인 성공 시 JWT를 생성해 `Authorization` 헤더와 응답 본문에 반환
* JWT에는 `username`, `role` 클레임을 저장
* 요청 시 `JWTFilter`가 토큰을 검증하고 `SecurityContext`에 인증 정보 설정
* Redis는 TTL 기반 데이터 저장 테스트 용도로 구성

---

## Security Flow

1. `/join`으로 회원가입 요청
2. `/login`으로 로그인 요청
3. 인증 성공 시 JWT 발급
4. 이후 요청에서 `Authorization: Bearer {token}` 전달
5. `JWTFilter`에서 토큰 검증 및 인증 정보 설정
6. 권한이 필요한 요청은 Spring Security가 인가 처리

---

## Considerations

* 세션 기반이 아닌 JWT 기반 Stateless 인증 구조 적용
* `LoginFilter`와 `JWTFilter`를 직접 필터 체인에 등록
* CORS 설정에서 `http://localhost:3000` 허용 및 `Authorization` 헤더 노출
* Redis는 인증 토큰 저장이 아닌 TTL 데이터 저장 테스트용으로 분리

---

## Limitations & Improvements

* Refresh Token 발급 및 저장 기능 미구현
* 로그아웃 및 토큰 블랙리스트 처리 미구현
* 입력값 검증 및 예외 처리 보완 필요
* Redis와 인증 구조 완전 통합 필요

---

## Future Plans

* Refresh Token 재발급 API 구현
* Redis 기반 로그아웃 / 블랙리스트 처리
* Access / Refresh Token 구조 분리
* 예외 응답 통일 및 보안 강화

---

## Notes

이 프로젝트는 완성형 서비스가 아니라   
JWT 인증/인가 구조와 Spring Security 동작을 이해하기 위한 학습 프로젝트입니다.

이후 프로젝트에서는 보안, 인증 흐름, 예외 처리까지 확장할 계획입니다.
