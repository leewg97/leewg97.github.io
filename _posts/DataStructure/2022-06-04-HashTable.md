---
title:  "[DataStructure] HashTable 이론 정리" 

categories:
  - DataStructure
tags:
  - [DataStructure, HashTable]

toc: true
toc_sticky: true

date: 2022-06-04
last_modified_at: 2022-06-04
---

## HashTable


****해쉬 테이블****

-   키(Key)에 데이터(Value)를 매핑할 수 있는 데이터 구조
-   Key를 통해 데이터 접근으로 속도 빠름
-   해쉬 함수(Hash Function): 임의의 데이터를 고정된 길이의 값으로 리턴해주는 함수

**장단점**

-   장점
    -   데이터 저장/읽기 속도가 빠름
    -   키에 대한 데이터가 있는지 확인이 쉬움
-   단점
    -   일반적으로 저장공간이 좀 더 많이 필요
    -   **여러 키에 해당하는 주소가 동일할 경우 충돌을 해결하기 위한 별도 자료구조가 필요**

\[예제\]문자열의 앞글자를 숫자로 변환해서, hashTable 의 길이로 나누어 나머지값을 리턴

```java
public int hashFunction(String key){
	return(int)(key.charAt(0)) % this.hashTable.lenghth();
}
```

-   객체 배열 선언할 때, 주소를 담을 수 있는 공간만 할당

```java
Slot[] hashTable = new Slot[100];
hashTable[0] = new Slot("TEST");
System.out.println(hashTable[0]);
System.out.println(hashTable[0].value);
```

→ 결과 1번은 주소가 나오고 2번은 “TEST” 출력

-   데이터 저장 메서드

```java
public boolean save(String key, String value){
	int address = this.hashFunction(kry);
	if(this.hashTable[address] != null){
		this.hashTable[address].value = value;
	}else{
		this.hashTable[address] = new Slot(value);
	}
	return true;
}
```

-   데이터를 가져오는 메서드(key 값으로 접근)

```java
public String det(String key){
	int address = this.hashFunction(key);
	if(this.hashTable[address] != null){
		return this.hashTable[address].value;
	}else{
		return null;
	}
}
```
