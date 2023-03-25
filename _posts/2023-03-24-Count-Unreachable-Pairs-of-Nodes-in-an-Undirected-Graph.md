---
layout:     post
title:      LeetCode 2316 Count Unreachable Pairs of Nodes in an Undirected Graph (Python)
number:     2316
level:      Medium
lcurl:      count-unreachable-pairs-of-nodes-in-an-undirected-graph/description
youtube:    3BnuMCHViMg
bilibili1:  
xigua:      
date:       2023-04-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
    - DFS
---

### 题目

You are given an integer n. There is an undirected graph with n nodes, numbered from 0 to n - 1. You are given a 2D integer array edges where edges[i] = [ai, bi] denotes that there exists an undirected edge connecting nodes ai and bi.

Return the number of pairs of different nodes that are unreachable from each other.

### 解题思路

使用bfs/dfs求出每个连通分量里节点的个数，这些点与图中所有的点都可以构成不可相互到达的点对。

### 代码
```python
class Solution:
    def countPairs(self, n: int, edges: List[List[int]]) -> int:
        edge = defaultdict(list)
        for x, y in edges:
            edge[x].append(y)
            edge[y].append(x)
        visited = set()
        res, rem = 0, n
        for i in range(n):
            if i in visited:
                continue
            s = [i]
            visited.add(i)
            tmp = 1
            while s:
                cur = s.pop()
                for nei in edge[cur]:
                    if nei not in visited:
                        s.append(nei)
                        visited.add(nei)
                        tmp += 1
            rem -= tmp
            res += tmp * rem
        return res
```
