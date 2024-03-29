---
title:  "[DataStructure] Stack & Queue 이론 정리" 

categories:
  - DataStructure
tags:
  - [DataStructure, Stack, Queue]

toc: true
toc_sticky: true

date: 2022-06-03
last_modified_at: 2022-06-03
---

---
## 자료구조 알고리즘

자료(data)와 자료구조(data structure)

→ 음식 과 그릇으로 접근하면 이해가 쉬움

알고리즘 : 문제를 풀기 위한 절차

### 빅오 표기법

검색에 소요되는 시간에 따라 하한 ~ 상한

하한 / 상한 / 하한 상한 : 상한점은 빅오 표기법, 하한점은 오메가 표기법, 상한/하한은 세타
<br><br>
**Big-O의 특징**

-   O(1) < O(logN) < O(N) < O(NlogN) < O(N2) < O(2N)

**점근표기법**

-   가장 큰 영향력이 있는 항만 표시
    -   O(N3 + N2 + N) -> O(N3)

**시간복잡도**

-   데이터 처리에 소요되는 시간
-   데이터 야의 변화에 따른 소요 시간의 변화
-   지연 장애가 발생했을 때 왜 발생했는지를 찾을 수 있는 근거
-   O(1) : 가장 짧은 시간이 걸림
-   O(N) : 데이터 크기에 비례함(대표적으로 for문)
-   O(N^2) : 이중 for문
-   O(logN)
    -   Ex) 1 ~ 100 숫자 중 상대방이 생각한 숫자를 맞출 때 가장 효율적으로 생각한 숫자를 맞추는 방법 : 50을 기준으로 절반씩 잘라내며 좁혀나가면 된다. ∴중앙값을 기준으로 살펴보는 것. 이것을 \*\*이진탐색(Binary search)\*\*이라고 한다
    -   **n** → **n/2 → n/2 \* 1/2** = **n/4** → **n/4 \* 1/2 = n/8** →……→ **(1/2)^k \* n ≈ 1 → n≈2^k**
    -   밑이 2인 log → logn = k(시행 횟수) → k번의 시행 → logn의 시간복잡도를 가짐
-   O(NlogN)
    -   Merge sort : 주어진 data 집합에서 절반씩 나누며 분할하는 과정 (이때 logn의 시간복잡도를 먼저 갖게 됨) → 하나씩 값을 비교하는 과정 → 이때 데이터 갯수인 N번만큼 비교하게 되므로 NlogN이 됨

<br>

## Stack

-   후입선출(Last-In-Fist-Out : LIFO)
    -   ex) ctrl + z / 인터넷 뒤로가기
-   데이터를 넣는 작업 : push()
-   데이터를 빼는 작업 : pop()
-   데이터를 그대로 둔 채 가장 위에 있는 데이터를 가지고 오는 것 : top(), peek()<어떤 데이터가 있는지 확인만>
<br><br>

## Queue

-   선입선출(First-In-Fast-Out : FIFO)
-   순서를 보장하는 프로그램
    -   ex) 사람이 몰린 이벤트 프로그램
-   push(), offer(), add() → data를 넣는 작업
    -   pop(), poll() → data를 빼는 작업
-   peek() → data를 확인하는 작업
-   enqueue : 데이터가 입력되는 동작
-   dequeue : 데이터가 빠지는 동작 → size찍어보면 dequeue 할 때마다 하나씩 줄어듬
-   제일 뒤 : rear 앞 : front

### Queue구현 방법

1.  LinkedList를 이용한 구현
2.  배열을 이용한 원형 큐 구현 : 배열로 구현하되 배열 구현의 단점 보완한 구조
       - 배열을 이용한 선형 큐 구현은 비효율적
3.  원현 큐 : 원형 큐에서는 한칸의 DUMMY공간을 주어서 꽉찬 상태와 비어있는 상태를 구분할 수 있음. front와 rear의 위치가 동일하면 비어있는 것임. front 위치 = rear 위치 +1 ⇒ 꽉찬상태
    - 고정된 크기의 배열로 구현
    - 원형 큐에서 인덱스로 접근할 때 인덱스 값의 큐 사이즈를 모듈로 연산 한 값으로 접근
    - isFull() , isEmpty()