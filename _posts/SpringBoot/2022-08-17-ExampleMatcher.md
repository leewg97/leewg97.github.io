---
title:  "[JPA] ExampleMatcher" 
excerpt: "JPA"


categories:
  - SpringBoot
tags:
  - [Java, SpringBoot, JPA]

toc: true
toc_sticky: true

date: 2022-08-17
last_modified_at: 2022-08-17
---

## [JPA] ExampleMatcher
현재 USERS TABLE에 삽입되어져 있는 데이터
![](https://velog.velcdn.com/images/leewg97/post/06213d82-f35e-4995-a2df-2290613fdb8e/image.png)

## 예제 코드
```java
    void crud() {
        ExampleMatcher matcher = ExampleMatcher.matching()
                .withIgnorePaths("name") // 무시
                .withMatcher("email", endsWith()); // "gmail.com"을 endsWith()로 감색

        Example<User> example = Example.of(new User("ch", "gmail.com"), matcher);

        userRepository.findAll(example).forEach(System.out::println);
    }
```

## 결과
```
Hibernate: 
    select
        user0_.id as id1_0_,
        user0_.createdAt as createda2_0_,
        user0_.email as email3_0_,
        user0_.name as name4_0_,
        user0_.updatedAt as updateda5_0_ 
    from
        USERS user0_ 
    where
        user0_.email like ? escape ?
User(id=1, name=chris, email=chris@gmail.com, createdAt=2022-08-17T17:01:34.664086, updatedAt=2022-08-17T17:01:34.664086)
User(id=2, name=nick, email=nick@gmail.com, createdAt=2022-08-17T17:03:14.576168, updatedAt=2022-08-17T17:03:14.576168)
User(id=3, name=ramy, email=ramy@gmail.com, createdAt=2022-08-17T17:03:14.576168, updatedAt=2022-08-17T17:03:14.576168)
User(id=4, name=sadik, email=sadik@gmail.com, createdAt=2022-08-17T17:03:14.576168, updatedAt=2022-08-17T17:03:14.576168)
User(id=7, name=deiu, email=deiu@gmail.com, createdAt=2022-08-17T17:15:13.098719, updatedAt=2022-08-17T17:15:13.098719)
User(id=8, name=ronny, email=ronny@gmail.com, createdAt=2022-08-17T17:15:13.098719, updatedAt=2022-08-17T17:15:13.098719)

```