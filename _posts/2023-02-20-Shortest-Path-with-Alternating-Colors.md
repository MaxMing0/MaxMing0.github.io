---
layout:     post
title:      LeetCode 1129 Shortest Path with Alternating Colors (Python)
number:     1129
level:      Medium
lcurl:      shortest-path-with-alternating-colors
youtube:    onkY4PR46GU
bilibili1:  
xigua:      
date:       2023-02-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
    - BFS 
---

### 题目

You are given an integer n, the number of nodes in a directed graph where the nodes are labeled from 0 to n - 1. Each edge is red or blue in this graph, and there could be self-edges and parallel edges.

You are given two arrays redEdges and blueEdges where:

redEdges[i] = [ai, bi] indicates that there is a directed red edge from node ai to node bi in the graph, and
blueEdges[j] = [uj, vj] indicates that there is a directed blue edge from node uj to node vj in the graph.
Return an array answer of length n, where each answer[x] is the length of the shortest path from node 0 to node x such that the edge colors alternate along the path, or -1 if such a path does not exist.

### 解题思路

把每个点分成两个点，从红边到和从蓝边到，然后用bfs求到每个点的最短路，最后在把两个点的结果合起来去较小值

### 代码
```python
class Solution:
    def shortestAlternatingPaths(self, n: int, red_edges: List[List[int]], blue_edges: List[List[int]]) -> List[int]:
        G = [[[], []] for i in range(n)]
        for i, j in red_edges: 
            G[i][0].append(j)
        for i, j in blue_edges: 
            G[i][1].append(j)
        res = [[0, 0]] + [[n * 2, n * 2] for i in range(n - 1)]
        q = deque([[0, 0], [0, 1]])
        while q:
            i, c = q.popleft()
            for j in G[i][c]:
                if res[j][c] == n * 2:
                    res[j][c] = res[i][1 - c] + 1
                    q.append([j, 1 - c])
        return [x if x < n * 2 else -1 for x in map(min, res)]
```
