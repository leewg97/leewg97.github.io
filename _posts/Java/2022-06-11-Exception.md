---
title:  "[Java] Exception : 예외" 
excerpt: "Exception"


categories:
  - Java
tags:
  - [Java, Exception]

toc: true
toc_sticky: true

date: 2022-06-11
last_modified_at: 2022-06-11
---

## 예외의 구조

![](https://velog.velcdn.com/images/leewg97/post/f12f9940-bdfe-4edd-97d7-f89d0753a8e1/image.png)

## 대표적인 예외 종류

---

| IOException | 입출력 동작 실패 또는 인터럽트 시 발생 |
| --- | --- |
| SQLException | 데이터베이스 연동 과정에서 문제가 발생했을 때 |
| NumberFormatException | 숫자 형식이 아닌 데이터를 숫자로 변경하려고 했을 때 |
| ArrayIndexOutOfBoundsException | 배열과 유사한 자료구조에서 인덱스의 범위를 벗어나는 경우/존재하지 않는 배열 공간을 사용하려고 했을 때 |
| ArithmeticException | 정수를 0으로 나눌때 발생 |
| ClassCastException | 변환할 수 없는 타입으로 객체를 변환할 때 발생 |
| NullPointerException | 주소가 할당되지 않은 참조변수를 사용하려 했을 때 |
| ClassNotFoundException | 존재하지 않는 클래스를 사용하려고 했을 때 |
| UnsupportedOperationException | 객체가 메소드를 지원하지 않는 경우 발생 |
| InterruptedException | Thread.sleep(), join(). Object의 wait()로 non-runnable 상태인 thread를 Runnable하게 만들 수 있도록 사용할 수 있음 |
| FileNotFoundException | 참조하는 파일이 지정된 위치에 존재하지 않는 경우 |


1.  예외처리(try ~ catch) : **사용자가 뭘 잘못했는지 알려주는 것**
    
    - JVM은 문제가 발생되는 상황에 해당하는 예외 클래스의 객체를 생성하여 실행중인 프로그램에 던짐(throw)
    - 던져진 예외객체는 처리해야 하는데 이 과정을 예외를 잡는다(catch)고 표현함
    - try ~ catch문은 가장 기본적인 방법
    
    ```java
    try{
        예외가 발생할 수 있는 코드 부분
    }catch(처리할 예외 타입 e){
    	try블록 안에서 예외가 발생했을 때 예외를 처리하는 부분
    }
    ```
    
2.  예외가 여러개 ? → **다중 catch문**
    - 발견된 예외 처리 방법 두가지!
        - 예외를 처리할 catch문 추가
        - 모든 Exception클래스의 최상위 부모인 Exception 타입의 catch문 맨 뒤에 추가 
            → **무조건 Exception 타입의 catch문은 맨 마지막에 넣어야 함 : 맨 위에서 잡으면 그 아래 catch는 의미가 없음**
        - detail하게 예외를 잡아주는 것이 원칙

3.  finally 블록
    - 예외와는 상관없이 무조건 실행 됨.
    - 일반적으로는 예외 처리 로직이 종료되기 전에 실행이 되어야만 하는 코드를 작성
    - 나중에 입출력, db연동에 반드시 사용해야 함
 
4.  throws 예약어
    - 메소드 오른쪽에 붙임
    - 여러 예외들을 예외 처리보다는 발생한 예외 객체를 양도하는 것
    - 현제 매소드에서 예외처리하는 것이 어려운 상활일 때 현재 메소드를 호출한 쪽으로 발생한 예외 객체를 넘길 수 있음
    - 잘 이용하면 예외처리 로직을 한 곳에 집중 가능

5.  throw 예약어
    - throw new \_\_\_\_\_\_\_\_\_\_();
    - 메소드 안에서 아무 곳에서나 사용 가능
    - 내가 원하는 시점에 하나의 예외 객체를 강제적으로 발생시켜 더 이상 프로그램이 진행되지 않도록 하는 것