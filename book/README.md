# Spring Boot + Thymeleaf Book Rental Project

Spring Boot + Thymeleaf 기반의 도서 대여 학습 프로젝트입니다.

회원, 도서, 작가, 장르, 대여 데이터를 관리하는 기능을 구현하며 MVC 구조와 JPA 기반 CRUD 흐름을 학습했습니다.

---

## Overview

이 프로젝트는 Spring Boot 기반 웹 애플리케이션의 전체 흐름을 익히기 위해 진행한 학습용 프로젝트입니다.

단순한 화면 구현을 넘어,

* Controller → Service → Repository 계층 분리
* JPA 엔티티 설계 및 연관관계 매핑
* Thymeleaf 기반 서버 사이드 렌더링
* 도서 대여 및 반납 흐름 구현

까지 직접 구성하는 데 초점을 두었습니다.

---

## Learning Goals

* Spring Boot MVC 구조 및 프로젝트 구성 이해
* Thymeleaf 기반 서버 사이드 렌더링 흐름 학습
* Spring Data JPA를 활용한 CRUD 구현
* 도메인 간 연관관계(도서-작가-장르-대여-회원) 설계 경험

---

## Tech Stack

| Category   | Technology                  |
| ---------- | --------------------------- |
| Language   | Java 17                     |
| Framework  | Spring Boot 3.4.4           |
| Template   | Thymeleaf                   |
| ORM        | Spring Data JPA (Hibernate) |
| Database   | MySQL                       |
| Build Tool | Gradle                      |
| Library    | Lombok                      |
| IDE        | IntelliJ IDEA               |

---

## Directory Structure

```text
book/
├─ src/main/java/com/pye/book/
│  ├─ controller/
│  ├─ entity/
│  ├─ repository/
│  ├─ service/
│  └─ PyeBookApplication.java
├─ src/main/resources/
│  └─ templates/
├─ build.gradle
└─ README.md
```

---

## Key Features

### User Management

* `/users` : 회원 목록 조회
* `/users/save` : 회원 등록 폼
* `POST /users` : 회원 등록 처리
* `/users/{id}/edit` : 회원 수정 폼
* `POST /users/update` : 회원 정보 수정
* `/users/{id}/delete` : 회원 삭제

### Book Management

* `/books` : 도서 목록 조회
* `/books/save` : 도서 등록 폼
* `POST /books/save` : 도서 등록 처리
* `/books/{id}/edit` : 도서 수정 폼
* `POST /books/update` : 도서 수정 처리
* `/books/{id}/delete` : 도서 삭제

### Author / Genre Management

* `/authors` : 작가 목록 조회
* `/authors/save` : 작가 등록
* `/genres` : 장르 목록 조회
* `/genres/save` : 장르 등록

### Rental Management

* `/rentals` : 대여 목록 조회
* `/rentals/save` : 대여 등록 폼
* `POST /rentals/save` : 대여 처리
* `POST /rentals/{id}/return` : 반납 처리

---

## Implementation Details

* 도서 등록 및 수정 시 작가와 장르를 선택하여 연관관계를 함께 저장
* 대여 등록 시 회원과 도서를 조회한 뒤 `rentalDate`, `dueDate`를 설정하여 저장
* 반납 시 `returnDate`를 저장하는 방식으로 반납 상태를 처리
* 회원 등록 시 `createdAt`을 `LocalDate.now()`로 저장
* 삭제 후에는 `redirect:`를 사용해 목록 페이지로 이동

---

## Domain Design

* `Book`은 `Author`, `Genre`와 `ManyToOne` 관계를 가집니다.
* `Rental`은 `User`, `Book`과 `ManyToOne` 관계를 가집니다.
* `User`는 이메일에 unique 제약이 적용되어 있습니다.
* `Book`에는 제목, ISBN, 출판사, 재고, 출간일 정보가 포함됩니다.
* `Rental`에는 대여일, 반납예정일, 반납일 정보가 포함됩니다.

---

## Considerations

* 도서 등록/수정 시 작가와 장르 엔티티를 직접 조회해 연결하도록 구현
* 반납 기능은 삭제가 아니라 `returnDate`를 기록하는 방식으로 처리
* 삭제 후 흐름 제어를 위해 `redirect:` 사용

---

## Limitations & Improvements

* 로그인 및 인증/인가 기능 미구현
* 도서 검색, 필터링, 페이징 기능 미구현
* 연체 계산 및 미반납 관리 기능 미구현
* 입력값 검증 및 글로벌 예외 처리 미적용

---

## Future Plans

* 도서 검색 / 필터링 / 페이징 기능 추가
* 미반납 및 연체 상태 관리 기능 추가
* 로그인 및 관리자 권한 기능 추가
* 예외 처리 및 입력 검증 로직 보완
* REST API 구조로 확장

---

## Notes

이 프로젝트는 완성형 서비스보다는 도서 관리와 대여 흐름을 중심으로   
Spring Boot 웹 애플리케이션 구조를 학습하기 위한 프로젝트입니다.

이후 프로젝트에서는 인증, 검색, 예외 처리, 확장성을 고려한 방향으로 발전시키고 있습니다.
