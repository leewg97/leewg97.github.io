---
title:  "[DataStructure] LinkedList 이론 정리" 

categories:
  - DataStructure
tags:
  - [DataStructure, LinkedList]

toc: true
toc_sticky: true

date: 2022-06-04
last_modified_at: 2022-06-04
---

### Linked List


: Node라는 객체로 구성되어 있음

-   Node는 date를 저장할 수 있는 field와 다음 Node를 가르킬 수 있는 Next Pointer field로 구성되어 있음
-   이 Node들이 다 연결 된 형태를 Linked List라고 함

가장 앞을 Head, 가장 뒤를 Tail이라고 하며 Tail의 Next point는 없으므로 Null

-   검색
    -   Array랑 다르게 Index를 통한 랜덤 엑세스가 불가함
    -   자신을 가르키고 있는 Next Pointer를 통해서만 접근 가능
    -   N개의 node를 가지고 있는 linked list의 검색의 시간 복잡도는 O(N) → 찾아가고자 하는 위치를 Head부터 Tail까지 순회하면서 찾아야 함
-   추가
    -   앞에서부터 하나씩 찾으며 끝 Node까지 가서 Null을 가르키고 있는 Pointer에 추가하고자 하는 데이터를 넣어야 하기 때문에 O(N)의 시간복잡도를 갖게됨
-   삽입
    -   중간에 넣을시 데이터를 다 밀어 줄 필요는 없음. 간단히 pointer만 조금 바꿔주면 됨
    -   하지만 삽입을 위한 과정의 시간복잡도는 O(N)
    -   head에 삽입하는 경우 : head의 pointer만 수정하면 되서 간단함
-   삭제
    -   삭제하고자 하는 node를 찾아가는 과정은 O(N)
    -   arraylist와 다르게 pointer만 조금 바꿔주면 됨
    -   삭제하고자 하는 node를 기준 previous node를 삭제하고자하는 node의 next node를 가르키게 하면 됨
-   장점
    -   배열의 복사나 재할당없이 데이터 추가 가능하며 자기가 쓰는 공간 만큼 유연하게 가능
-   단점
    -   데이터 접근에 대한 시간이 늘어남 O(N)

**더미노드**

-   Head부터 데이터를 넣는 것이 아니라 Head는 어떤 상황에도 데이터를 넣지 않음
-   Head를 넘어서부터 데이터를 넣는 것
-   코드의 구현에 있어 간결해짐

### DoubleLinkedList

-   LinkedList와 다르게 Head 와 Tail을 각각 따로 갖게 됨
-   next와 prev를 함께 갖고 있음 : prev를 위한 공간을 더 사용한다는 의미
-   첫 초기화 & 아무 데이터도 들어오지 않았을 때
    -   HEAD dummy 와 TAIL dummy존재
    -   Head의 next는 Tail/Tail의 prev는 Head
-   Tail을 통해 한번에 가능 / 시간 복잡도 O(1)
-   검색 : 절반을 나눠 가까운 쪽에서 접근