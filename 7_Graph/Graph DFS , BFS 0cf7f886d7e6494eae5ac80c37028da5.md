# Graph : DFS , BFS

## GRAPH algorithms

### Graph basics

exp : routing , clustering, detection….

### Graph basics

- **Undirected Graphs : 방향 X**
    - vertices(vertex) / edges(edge) : 정점 / 간선
        - vertex 4의 degree (차수) : 2 (vertex 4의 2 edges)
        - vertex 4의 neightbors (이웃) / adjacent (인접 vertex) : 2 and 3 vertex
        
        ![스크린샷 2023-05-03 오후 6.25.12.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.25.12.png)
        
- **Directed Graphs : 방향 O**
    - 방향성 - E case 추가됨 (3,4) , (4,3)
        - in-degree (입-차수) of vertex 4 :  2
        - out-degree (출-차수) of vertex 4 :  1
        - incoming neighbors of vertex 4 : 2,3
        - outgoing neighbors of vertex 4: 3
    
    ![스크린샷 2023-05-03 오후 6.25.21.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.25.21.png)
    

### How to represent graphs

1. matrix 
    
    ![스크린샷 2023-05-03 오후 6.29.54.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.29.54.png)
    
2. linked lists
    
    ![스크린샷 2023-05-03 오후 6.29.30.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.29.30.png)
    

- vertex에 특성 저장 ( name , IP adress)
- edge membership? neighbor query? - 어떻게 찾을 수 있나..

### Trade-offs

n: vertices / m edges

|  | matrix | linked list |
| --- | --- | --- |
| Edge membership : is e = {v,w} in E? | O(1) | O(deg(v)) or O(deg(w)) |
| Neighbor query | O(n) | O(deg(v)) |
| Space requirements |  O(n^2) | O(n+m) |

### DFS / BFS 개요

![스크린샷 2023-05-03 오후 6.34.32.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.34.32.png)

### 원하는 것이 많을 때 → 탐색으로 찾음

### DFS : depths 깊이탐색

: **깊은 곳 우선 탐색 →** stack 인접노드 (python : list )

Running time : O(n+m) : n : the number of edges v : the number of vertices

![스크린샷 2023-05-08 오후 2.00.20.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.00.20.png)

**IN DFS : Topological sorting : 위상 정렬** 

→ 방향성 O, cycle X

topological ordering : 위상 순서 

> Definition: The topological ordering of a DAG is an ordering of its vertices such that for every directed edge (u, v) ∈ E, u precedes v in the ordering. → ((u,v) 간선이 있으면, u 가 v보다 앞의 순서를 가진다.
> 

→ 깊이에 대한 순서 정의를 위해 (내 이해임)

google : **Parenthesis Theorem** is used in DFS of graph. ***It states that the descendants in a depth-first-search tree have an interesting property***.

**PROVE THIS: if A → B , then B.finishTime < A.finishTime**

CASE 1 : B = A’s child

![스크린샷 2023-05-08 오후 2.10.56.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.10.56.png)

CASE 2 : B is not descendant of A / We must be explored B before A!!!!! → Otherwise B먼저 방문 X → CASE 1과 동일함 

![스크린샷 2023-05-08 오후 2.14.58.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.14.58.png)

![스크린샷 2023-05-08 오후 2.16.25.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.16.25.png)

### BFS : 너비 탐색

: queue 가까운 노드 구현 (python :dequeue)

![스크린샷 2023-05-08 오후 2.31.25.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.31.25.png)

![스크린샷 2023-05-08 오후 2.31.34.png](Graph%20DFS%20,%20BFS%200cf7f886d7e6494eae5ac80c37028da5/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_2.31.34.png)

Running time : O(n+m) : n : the number of edges v : the number of vertices

Application : 최단경로 구하기 Shortest path on unweighted graph

### 🌟 NETWORK : Shortest path finding

1. Dijkstra
2. Bellman Ford - BF