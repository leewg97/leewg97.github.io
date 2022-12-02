---
title:  "[SpringBatch] Spring Batch Architecture" 
excerpt: "SpringBatch"

categories:
  - Spring
tags:
  - [Java, Spring, SpringBatch, Windows, Gradle]

toc: true
toc_sticky: true

date: 2022-12-02
last_modified_at: 2022-12-02
---

## Spring Batch Architecture
* Spring Batch는 확성성 및 다양한 사용자의 유형을 고려하여 설계했다.
* 아래 그림은 Spring Barch의 계층 구조이다.

![image](https://user-images.githubusercontent.com/77063888/205103163-b6257b23-9d73-4d5e-85a1-d8f38789e2d1.png)

그림에서 보다시피 세 가지의 주요 컴포넌트가 있다.
* Application : Spring Batch를 사용하는 개발자가 만드는 모든 Batch Job과 Custom Code를 포함한다.
* Batch Core : Job을 실행하고 제어하는데 필요한 핵심 Runtime class를 포함한다. `JobLauncher`, `Job`, `Step` 구현체 또한 포함된다.
* Batch Infrastructure : 공통 reader와 writer, service(ex. `RetryTemplate`)를 포함하는데, application 개발자와 core framework 자체에서 활용하기도 한다.


### Reference
* https://docs.spring.io/spring-batch/docs/4.2.x/reference/html/index-single.html#batchArchitectureConsiderations