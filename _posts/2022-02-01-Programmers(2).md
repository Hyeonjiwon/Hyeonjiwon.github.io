---
title: '[Programmers] 깊이/너비 우선 탐색 BFS/DFS' 
excerpt: "코딩테스트 고득점 Kit"
categories:
    - Algorithm
    - JAVA
    - Python

tag:
    - Programmers
    - Algorithm
    - BFS
    - DFS
    - python

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2022-02-01T17:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## 타겟 넘버 

__문제__


__제한사항__

- 

__입출력 예__

| array                 | commands                          | return    |
| --------------------- | --------------------------------- | --------- |
| [1, 5, 2, 6, 3, 7, 4] | [[2, 5, 3], [4, 4, 1], [1, 7, 3]] | [5, 6, 3] |

__풀이__

```python
def solution(numbers, target):
    answer = 0
    leaves = [0]
        
    for num in numbers:
        tmp = []
        
        for parent in leaves:
            tmp.append(parent + num)
            tmp.append(parent - num)

        leaves = tmp
        
    for leaf in leaves:
        if leaf == target:
            answer += 1
    
    return answer
```


- itertools의 product 사용하기 
  
```python
from itertools import product

def solution(numbers, target):
    answer = 0
    n_list = [(x, -x) for x in numbers]
    product_n = list(map(sum, product(*n_list)))
    
    for n in product_n:
        if n == target:
            answer += 1
            
    return answer
```

- return 할때 list.count(target) 사용하기
   
```python
from itertools import product

def solution(numbers, target):
    answer = 0
    n_list = [(x, -x) for x in numbers]
    product_n = list(map(sum, product(*n_list)))
          
    return product_n.count(target)
```


## 네트워크

__문제__


__제한사항__

- 

__입출력 예__

| array                 | commands                          | return    |
| --------------------- | --------------------------------- | --------- |
| [1, 5, 2, 6, 3, 7, 4] | [[2, 5, 3], [4, 4, 1], [1, 7, 3]] | [5, 6, 3] |

__풀이__

- visited = [1, ,1, 1]  인 경우 모든 네트워크가 하나로 연결 되어 있는 거임
- 각 컴퓨터의 연결 정보와 visited를 비교  
  
```python
from collections import deque

def solution(n, computers):
    answer = 0
    visited = [0] * n    

    while 0 in visited:
        x = visited.index(0)
        queue = deque([x])
        visited[x] = 1
        
        while queue:
            v = queue.popleft()
            
            for i in range(n):
                if visited[i] == 0 and computers[v][i] == 1:
                    queue.append(i)
                    visited[i] = 1
        answer += 1  
        
    return answer
```


## 참고

> [출처: 프로그래머스 코딩 테스트 연습](https://programmers.co.kr/learn/challenges)

<br>

## 

__문제__


__제한사항__

- 

__입출력 예__

| s      | return |
| ------ | ------ |
| "a234" | false  |
| "1234" | true   |

__풀이__

```python

```

<br>