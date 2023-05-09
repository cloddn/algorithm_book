# DP part 1

## Dynamic programming: 동적 프로그래밍 = 동적 계획법

- Bellman-Ford algorithm
- Fibonacci Numbers
- Floyd-Warshall algorithm

### another problems :

- Longest Common Subsequence
- Knapsack
- Independent sets

A weighted directed graph : 

1. weights on edges = costs
2. cost of a path is the sum of the weights
3. shortest path from s to t = smallest cost path from s to t
4. single-source shortest path problem is to find the shortest path form s to v -all v in the graph 

1. 다익스트라 알고리즘
2. 밸먼-포드 알고리즘 

⇒ 둘다 single - source shortest path in weighted graphs

![스크린샷 2023-05-08 오후 4.00.37.png](DP%20part%201%204aa54269a62a4df7a5aa04edb46d3d42/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-08_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.00.37.png)

⇒ 벨먼포드 vs 다익스트라 차이에 대해 유의 

벨먼포드: 각 루트를 선택한 이후 weights 업데이트 : For iu in V: