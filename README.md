# Spring Boot Backend Study

![Java](https://img.shields.io/badge/Java-007396?style=flat-square\&logo=openjdk\&logoColor=white)
![Spring Boot](https://img.shields.io/badge/SpringBoot-6DB33F?style=flat-square\&logo=springboot\&logoColor=white)
![Spring Security](https://img.shields.io/badge/SpringSecurity-6DB33F?style=flat-square\&logo=springsecurity\&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-6DB33F?style=flat-square\&logo=spring\&logoColor=white)
![Thymeleaf](https://img.shields.io/badge/Thymeleaf-005F0F?style=flat-square\&logo=thymeleaf\&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square\&logo=mysql\&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square\&logo=redis\&logoColor=white)

> Backend development portfolio based on Spring Boot

<br>

Spring Boot를 중심으로 웹 애플리케이션 구조, 도메인 설계, 인증/인가까지   
백엔드 개발 과정을 단계적으로 학습하며 구현한 프로젝트들을 정리한 저장소입니다.

이 저장소는 구름톤 유니브(9oormthonUNIV) 백엔드 스터디 과정에서 학습하며 구현한 프로젝트들을 정리한 것입니다.

---

## Project Overview

본 저장소는 단순 프로젝트 모음이 아니라,

* MVC 구조 이해
* JPA 기반 CRUD 구현
* 도메인 설계 및 서비스 로직 확장
* Spring Security + JWT 인증/인가

까지 이어지는 **백엔드 학습 흐름을 단계적으로 정리한 레포지토리**입니다.

각 프로젝트는 독립적으로 구성되어 있으며,   
기능과 구조를 점진적으로 확장하는 방식으로 학습을 진행했습니다.

---

## Projects

### 1. Spring Boot + Thymeleaf Member Management Project

회원 관리 기능을 중심으로 MVC 구조와 JPA CRUD를 학습한 프로젝트입니다.

#### Main Features

* 회원가입 / 로그인 / 수정 / 삭제
* Session 기반 인증 처리
* Controller / Service / Repository 계층 구조 설계

📁 [Member Management](member/)

---

### 2. Spring Boot + Thymeleaf Book Rental Project

도메인 설계를 기반으로 CRUD를 확장한 도서 대여 시스템입니다.

#### Main Features

* 도서 / 작가 / 장르 / 회원 / 대여 관리
* 도메인 간 연관관계 설계
* 대여 및 반납 흐름 구현

📁 [Book Rental Project](book/)

---

### 3. Spring Boot + JWT + Redis Security Project

Spring Security 기반 JWT 인증/인가를 구현한 프로젝트입니다.

#### Main Features

* JWT 발급 및 검증
* Stateless 인증 구조 적용
* Redis 기반 데이터 저장 및 캐시 테스트

📁 [JWT Security Project](jwtsecurity/)

---

## Learning Focus

이 저장소는 다음과 같은 흐름으로 학습을 진행합니다.

* MVC 구조 이해
* JPA 기반 CRUD 구현
* 도메인 설계 및 서비스 로직 확장
* Spring Security 인증/인가 적용
* JWT 기반 Stateless 구조 이해
* Redis 활용

---

## Repository Structure

```text id="root-final"
9oormthonUNIV
├── member
├── book
└── jwtsecurity
```

---

## Notes

이 저장소는 완성형 서비스가 아니라   
백엔드 개발을 단계적으로 학습하기 위한 프로젝트 모음입니다.

각 프로젝트를 통해 구조 → 기능 → 보안까지 확장하며   
실무에서 사용되는 기술 흐름을 이해하는 데 중점을 두었습니다.

