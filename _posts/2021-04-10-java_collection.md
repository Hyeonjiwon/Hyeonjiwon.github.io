---
title: '[JAVA] Java Collection 정리' 
excerpt: "Java Collections Framework "
categories:
    - JAVA

tag:
    - JAVA

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2021-04-10 T21:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## Java Collection Framework

- 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화된 방법을 제공하는 클래스의 집합을 의미

- 데이터를 저장하는 자료 구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현해 놓은것

- 인터페이스(interface)를 사용하여 구현

<br>

## Collection Framework의 계층 구조

![JavaCollection](https://user-images.githubusercontent.com/47733530/114268840-37d09b00-9a3e-11eb-8543-d37defc1b5d8.png)

- java.util.Collection
- java.util.Map

<br>

## List
순서 o 데이터의 집합, 데이터 중복 허용 o

**구현 클래스**
- ArrayList<E>
    - 내부적으로 배열을 이용하여 요소를 순차적으로 저장
    - 인덱스를 이용해 배열 요소에 빠르게 접근 가능
    - 요소의 추가 및 삭제 작업에 걸리는 시간이 김

    ```java
    ArrayList<Integer> arrList = new ArrayList<Integer>();
    
    // add() 메소드를 이용한 요소의 저장
    arrList.add(40);
    arrList.add(20);
    arrList.add(30);
    arrList.add(10);
    
    // for 문과 get() 메소드를 이용한 요소의 출력
    for (int i = 0; i < arrList.size(); i++) {
        System.out.print(arrList.get(i) + " ");
    }
    System.out.println();
    
    // remove() 메소드를 이용한 요소의 제거
    arrList.remove(1);
    
    // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
    for (int e : arrList) {
        System.out.print(e + " ");
    }
    System.out.println();
    
    // Collections.sort() 메소드를 이용한 요소의 정렬
    Collections.sort(arrList);
    
    // iterator() 메소드와 get() 메소드를 이용한 요소의 출력
    Iterator<Integer> iter = arrList.iterator();
    while (iter.hasNext()) {
        System.out.print(iter.next() + " ");
    }
    System.out.println();

    // set() 메소드를 이용한 요소의 변경
    arrList.set(0, 20);

    for (int e : arrList) {
        System.out.print(e + " ");
    }
    System.out.println();
    
    // size() 메소드를 이용한 요소의 총 개수
    System.out.println("리스트의 크기 : " + arrList.size());

    ```

- LinkedList<E>
    - 배열을 이용하는 ArrayList 클래스의 단점을 극복하기 위해 고안
    - 내부적으로 연결 리스트를 이용하여 요소를 저장
    - 저장된 요소가 비순차적으로 분포

    - 단일 연결 리스트(singly linked list)
        - 다음 요소를 가리키는 참조만을 가지는 연결 리스트
        - 요소의 저장, 삭제가 아주 빠르게 처리
        - 현재 요소에서 이전 요소로 접근하기 어려움

    - 이중 연결 리스트(doubly linked list)
        - 이전 요소를 가리키는 참조를 가지는 이중 연결 리스트가 더 많이 사용

    ```java
    LinkedList<String> lnkList = new LinkedList<String>();
		
    // add() 메소드를 이용한 요소의 저장
    lnkList.add("넷");
    lnkList.add("둘");
    lnkList.add("셋");
    lnkList.add("하나");
    
    // for 문과 get() 메소드를 이용한 요소의 출력
    for (int i = 0; i < lnkList.size(); i++) {
        System.out.print(lnkList.get(i) + " ");
    }
    System.out.println();
    
    // remove() 메소드를 이용한 요소의 제거
    lnkList.remove(1);
    
    // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
    for (String e : lnkList) {
        System.out.print(e + " ");
    }
    System.out.println();

    // set() 메소드를 이용한 요소의 변경
    lnkList.set(2, "둘");

    for (String e : lnkList) {
        System.out.print(e + " ");
    }
    System.out.println();
    
    // size() 메소드를 이용한 요소의 총 개수
    System.out.println("리스트의 크기 : " + lnkList.size());
    ```

- Vector<E>
    -  ArrayList 클래스와 같은 동작을 수행하는 클래스
    - 현재에는 기존 코드와의 호환성을 위해서만 남아있음
    - Vector 클래스보다는 ArrayList 클래스를 사용하는 것이 좋음

- Stack<E>
    - List 컬렉션 클래스의 Vector 클래스를 상속받음
    - 스택 메모리 구조의 클래스를 제공
    - 후입선출(LIFO)

    ```java
    Stack<Integer> st = new Stack<Integer>();	// 스택의 생성
    //Deque<Integer> st = new ArrayDeque<Integer>();
    
    // push() 메소드를 이용한 요소의 저장
    st.push(4);
    st.push(2);
    st.push(3);
    st.push(1);
    
    // peek() 메소드를 이용한 요소의 반환
    System.out.println(st.peek());
    System.out.println(st);
    
    // pop() 메소드를 이용한 요소의 반환 및 제거
    System.out.println(st.pop());
    System.out.println(st);
    
    // search() 메소드를 이용한 요소의 위치 검색
    System.out.println(st.search(4));
    System.out.println(st.search(3));
    ```

- Queue<E>
    - 선입선출(FIFO)   
    - Queue 인터페이스를 상속받는 하위 인터페이스
        1. Deque<E>
        2. BlockingDeque<E>
        3. BlockingQueue<E>
        4. TransferQueue<E>

    ```java
		LinkedList<String> qu = new LinkedList<String>();	// 큐의 생성
		//Deque<String> qu = new ArrayDeque<String>();
		
		// add() 메소드를 이용한 요소의 저장
		qu.add("넷");
		qu.add("둘");
		qu.add("셋");
		qu.add("하나");
		
		// peek() 메소드를 이용한 요소의 반환
		System.out.println(qu.peek());
		System.out.println(qu);
		
		// poll() 메소드를 이용한 요소의 반환 및 제거
		System.out.println(qu.poll());
		System.out.println(qu);
		
		// remove() 메소드를 이용한 요소의 제거
		qu.remove("하나");
		System.out.println(qu);   
    ```

<br>

__List 인터페이스 메소드__

| 메소드 | 설명 |
|--------|------|
| boolean add(E e) | 해당 리스트(list)에 전달된 요소 추가 (선택적 기능) |
| void add(int index, E e) | 해당 리스트의 특정 위치에 전달된 요소 추가 (선택적 기능) |
| void clear() | 해당 리스트의 모든 요소 제거 (선택적 기능) |
| boolean contains(Object o) | 해당 리스트가 전달된 객체를 포함하고 있는지 확인 | 
| boolean equals(Object o) | 해당 리스트와 전달된 객체가 같은지 확인 |
| E get(int index) | 해당 리스트의 특정 위치에 존재하는 요소 반환 |
| boolean isEmpty() | 해당 리스트가 비어있는지 확인 | 
| Iterator<E> iterator() | 해당 리스트의 반복자(iterator) 반환 |
| boolean remove(Object o) | 해당 리스트에서 전달된 객체 제거 (선택적 기능) |
| boolean remove(int index) | 해당 리스트의 특정 위치에 존재하는 요소 제거함 (선택적 기능) |
| E set(int index, E e) | 해당 리스트의 특정 위치에 존재하는 요소를 전달받은 객체로 대체 (선택적 기능) |
| int size() | 해당 리스트의 요소의 총 개수 반환 |
| Object[] toArray() | 해당 리스트의 모든 요소를 Object 타입의 배열로 반환 |

<br>

## Set
순서 x 데이터 집합, 데이터 중복 허용 x

**구현 클래스**
- HashSet

    ```java
    HashSet<String> hs01 = new HashSet<String>();
    HashSet<String> hs02 = new HashSet<String>();
    
    // add() 메소드를 이용한 요소의 저장
    hs01.add("홍길동");
    hs01.add("이순신");
    System.out.println(hs01.add("임꺽정"));
    System.out.println(hs01.add("임꺽정"));	// 중복된 요소의 저장
    
    // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
    for (String e : hs01) {
        System.out.print(e + " ");
    }
    System.out.println();
    
    // add() 메소드를 이용한 요소의 저장
    hs02.add("임꺽정");
    hs02.add("홍길동");
    hs02.add("이순신");
    
    // iterator() 메소드를 이용한 요소의 출력
    Iterator<String> iter02 = hs02.iterator();
    while (iter02.hasNext()) {
        System.out.print(iter02.next() + " ");
    }
    System.out.println();

    // size() 메소드를 이용한 요소의 총 개수
    System.out.println("집합의 크기 : " + hs02.size());
    ```

- TreeSet

    ```java
    TreeSet<Integer> ts = new TreeSet<Integer>();
    
    // add() 메소드를 이용한 요소의 저장
    ts.add(30);
    ts.add(40);
    ts.add(20);
    ts.add(10);

    // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
    for (int e : ts) {
        System.out.print(e + " ");
    }
    System.out.println();

    // remove() 메소드를 이용한 요소의 제거
    ts.remove(40);
    
    // iterator() 메소드를 이용한 요소의 출력
    Iterator<Integer> iter = ts.iterator();
    while (iter.hasNext()) {
        System.out.print(iter.next() + " ");
    }
    System.out.println();

    // size() 메소드를 이용한 요소의 총 개수
    System.out.println("이진 검색 트리의 크기 : " + ts.size());

    // subSet() 메소드를 이용한 부분 집합의 출력
    System.out.println(ts.subSet(10, 20));
    System.out.println(ts.subSet(10, true, 20, true));
    ```

<br>

__Set 인터페이스 메소드__

| 메소드 | 설명 |
|--------|------|
| boolean add(E e) | 해당 집합(set)에 전달된 요소 추가 (선택적 기능) |
| void clear() | 해당 집합의 모든 요소 제거 (선택적 기능) |
| boolean contains(Object o) | 해당 집합이 전달된 객체를 포함하고 있는지 확인 | 
| boolean equals(Object o) | 해당 집합과 전달된 객체가 같은지 확인 |
| boolean isEmpty() | 해당 집합이 비어있는지 확인 | 
| Iterator<E> iterator() | 해당 집합의 반복자(iterator) 반환 |
| boolean remove(Object o) | 해당 집합에서 전달된 객체 제거 (선택적 기능) |
| int size() | 해당 집합의 요소의 총 개수 반환 |
| Object[] toArray() | 해당 집합의 모든 요소를 Object 타입의 배열로 반환 |

<br>

## Map
키(key) - 값(value) 쌍으로 이루어진 데이터 집합, 순서 x
키(key) 중복 허용 x, 값(value) 중봅 허용 o

**구현 클래스**
- Hashtable

    ```java
    ```

- HashMap

    ```java
    ```

- TreeMap

    ```java
    ```

## 참고

> [tcpschool.com - 컬렉션 프레임워크의 개념](http://www.tcpschool.com/java/java_collectionFramework_concept)

> [API 사용법](https://docs.oracle.com/javase/8/docs/api/?java/util/Collection.html)

> [Java 하우투](https://www.delftstack.com/ko/howto/java/)