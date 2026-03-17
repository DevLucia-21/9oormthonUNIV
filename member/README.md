# Spring Boot + Thymeleaf Member Management Project

Spring Boot + Thymeleaf 기반의 회원 관리 학습 프로젝트입니다.

회원가입, 로그인, 조회, 수정, 삭제 등 기본적인 사용자 관리 기능을 구현했습니다.

---

## Overview

이 프로젝트는 Spring Boot 기반 웹 애플리케이션의 전체 흐름을 이해하기 위해 진행한 학습용 프로젝트입니다.

단순 기능 구현을 넘어, Controller → Service → Repository 계층 구조와   
DTO ↔ Entity 변환, JPA 기반 데이터 처리, 세션 기반 로그인 흐름까지 직접 구현하는 데 초점을 두었습니다.

---

## Learning Goals

* Spring Boot MVC 구조 및 프로젝트 구성 이해
* Thymeleaf 기반 서버 사이드 렌더링 흐름 이해
* Spring Data JPA를 활용한 CRUD 구현
* Controller → Service → Repository 계층 분리 설계

---

## Tech Stack

| Category   | Technology                  |
| ---------- | --------------------------- |
| Language   | Java 17                     |
| Framework  | Spring Boot 3.x             |
| Template   | Thymeleaf                   |
| ORM        | Spring Data JPA (Hibernate) |
| Database   | MySQL                       |
| Build Tool | Gradle                      |
| IDE        | IntelliJ IDEA               |

---

## Directory Structure

```text id="v7q3km"
member/
├─ src/main/java/com/Yeeun/member/
│  ├─ MemberApplication.java
│  ├─ controller/
│  ├─ service/
│  ├─ repository/
│  ├─ entity/
│  └─ dto/
├─ src/main/resources/
│  ├─ templates/
│  │  ├─ index.html
│  │  ├─ login.html
│  │  ├─ save.html
│  │  ├─ list.html
│  │  ├─ detail.html
│  │  ├─ update.html
│  │  └─ main.html
│  └─ application.yml
└─ build.gradle
```

---

## Key Features

### 회원 가입 & 로그인

* `/member/save` : 회원가입 폼 및 가입 처리
* `/member/login` : 로그인 폼 및 로그인 처리
* 로그인 성공 시 `HttpSession`에 사용자 이메일 저장하여 인증 상태 유지

### 회원 목록 & 상세 조회

* `/member/` : 전체 회원 목록 조회
* `/member/{id}` : 회원 상세 조회

### 프로필 수정 & 탈퇴

* `/member/update` : 회원 정보 수정
* `/member/delete/{id}` : 회원 삭제

### 기타 기능

* `/member/logout` : 로그아웃 (세션 무효화)
* `/member/email-check` : 이메일 중복 검사 (AJAX)

---

## Implementation Details

* Controller에서 요청을 받아 Service로 비즈니스 로직 위임
* Service에서 DTO ↔ Entity 변환 후 Repository 호출
* Spring Data JPA의 `save()`, `findBy...()` 메서드를 활용한 데이터 처리
* 로그인 상태는 `HttpSession`을 통해 관리

---

## Considerations

* **중복 제출 방지**

  * `redirect:` 사용으로 새로고침 시 중복 요청 방지

* **세션 기반 인증**

  * 로그인 시 세션에 사용자 이메일 저장
  * 로그아웃 시 `session.invalidate()`로 상태 초기화

---

## Limitations & Improvements

* 비밀번호 암호화 미적용 (보안 취약)
* 입력값 검증 로직 부족
* 예외 처리 및 사용자 피드백 개선 필요
* 권한 분리(관리자/사용자) 미구현

---

## Future Plans

* Spring Security 기반 인증/인가 적용
* 비밀번호 암호화 적용
* 이메일 인증 및 비밀번호 찾기 기능 추가
* REST API 구조로 확장 후 프론트엔드 분리

---

## Notes

이 프로젝트는 완성형 서비스보다는 회원 관리 기능을 중심으로    
Spring Boot 웹 애플리케이션의 기본 구조를 이해하는 데 목적이 있습니다.

이후 프로젝트에서는 보안, 구조 설계, 확장성을 고려한 방향으로 발전시키고 있습니다.
