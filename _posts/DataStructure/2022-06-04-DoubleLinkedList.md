---
title:  "[DataStructure] DoubleLinkedList 이론 정리" 

categories:
  - DataStructure
tags:
  - [DataStructure, DoubleLinkedList, LinkedList]

toc: true
toc_sticky: true

date: 2022-06-04
last_modified_at: 2022-06-04
---

## Double LinkedList


**더블 링크드 리스트(Doubly linked list) 기본 구조**

-   이중 연결 리스트라고도 함
-   장점: 양방향으로 연결되어 있어서 노드 탐색이 양쪽으로 모두 가능

**임의 Node 앞에 Node 추가**

```java
public boolean insertToFront(T existData, T addData){
		if(this.head == null){
			this.head = new Node<T> (addData);
			this.tail = this.head;
			return true;
		}else if(this.head.data == existeData){
			Node<T> newHead = new Node<T>(addData);
			newHead.next = this.head;
			this.head = newHead;
			return true;
		}else{
			Node<T> node = this.head;
			while(node != null){
				if(node.data == existeData){   //노드의 데이터를 찾으면
					Node<T> nodePrev =node.prev; //prev 노드를 nodePrev에 저장
					nodePrev.next = new Node<T>(addData); //새로운 노드를 nodePrev.next로 저장
					nodePrev.next.next = node; //기존 노드를 nodePrev.next.next로 저장 
					
					nodePrev.next.prev= nodePrev; //새로운 노드의 다음노드의 prev에 연결 (자기랑)
					node.prev =nodePrev.next; //node.prev의 다음노드를 기존 노드의 prev로 연결
					return true;
				}else{ //못찾으면 다음으로 넘어감 
					node =node.next;
				}
			}
			return false;
		}
	}
```

**\[다른 방법\]** : 반 쪼개서 임의 노드에 추가

```java
// 위에서 size 초기화 해둬야 함
public void insert(int index, T t){

        Node prev = null;
        Node curr = null;
        int i = 0;

        if(index < this.size / 2){
            prev = this.head;
            curr = this.head.next;
            while(i++ < index){
                prev = prev.next;
                curr = curr.next;
            }
        }else{
            curr = this.tail;
            prev = this.tail.prev;
            while(i++ < (this.size - index)){
                curr = curr.prev;
                prev = prev.prev;
            }
        }

        Node node = new Node(t, prev, curr);
        curr.prev = node;
        prev.next = node;
        this.size++;

    }
```