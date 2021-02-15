---
layout:     post
title:      LeetCode 785 Is Graph Bipartite (Python)
number:     785
level:      Medium
lcurl:      is-graph-bipartite
youtube:    DhcpRjHgP9A
bilibili1:  player.bilibili.com/player.html?aid=756634325&bvid=BV11r4y1P7Wr&cid=297955652&page=1
xigua:      
date:       2021-02-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Graph
---

### 题目

Given an undirected graph, return true if and only if it is bipartite.

Recall that a graph is bipartite if we can split its set of nodes into two independent subsets A and B, such that every edge in the graph has one node in A and another node in B.

The graph is given in the following form: graph[i] is a list of indexes j for which the edge between nodes i and j exists. Each node is an integer between 0 and graph.length - 1. There are no self edges or parallel edges: graph[i] does not contain i, and it doesn't contain any element twice.

### 解题思路

dfs进行染色，两个相邻的点颜色需要不同，如果出现矛盾，返回False

### 代码
```python
class Solution:
    def isBipartite(self, graph: List[List[int]]) -> bool:
        def dfs(v, c):
            color[v] = c
            for node in graph[v]:
                if color[node] == c:
                    return False
                if color[node] == 0 and not dfs(node, -c):
                    return False
            return True
        
        l = len(graph)
        color = [0] * l
        for i in range(l):
            if color[i] == 0:
                if not dfs(i, 1):
                    return False
        return True
```
