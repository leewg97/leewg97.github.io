---
title:  "[Spring] Spring Security" 
excerpt: "Spring Security"


categories:
  - Spring
tags:
  - [Java, Spring, Spring Security, Windows]

toc: true
toc_sticky: true

date: 2022-08-23
last_modified_at: 2022-08-23
---

## 스프링 시큐리티

### 시큐리티의 필요성
---
웹사이트는 서비스를 사용하는 유저들의 개인정보를 보호하고, 서버 리소스를 보호하기 위해 보안 정책을 설정해야 한다.

### 인증 (Authentication)
---
사이트에 접근하는 사람이 누구인지 시스템이 알아야 한다.<br> 
익명사용자(anonymous user)를 허용하는 경우도 있지만, 특정 리소스에 접근하거나 개인화된 사용성을 보장 받기 위해서는 반드시 로그인하는 과정이 필요하다.<br>
로그인은 보통 ```username```과 ```password``` 를 입력하고 로그인하는 경우와 SNS사이트를 통해 인증을 대리하는 경우가 있다.

- UsernamePassword 인증
  - Session 관리
  - 토큰 관리 (sessionless)
- SNS 로그인 (소셜 로그인) : 인증 위임
