---
layout:     post
title:      LeetCode 1579 Remove Max Number of Edges to Keep Graph Fully Traversable (Python)
number:     1579
level:      Hard
lcurl:      remove-max-number-of-edges-to-keep-graph-fully-traversable
youtube:    GVG7rQ3XPio
bilibili1:  
xigua:      
date:       2023-04-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
---

### 题目

Alice and Bob have an undirected graph of n nodes and three types of edges:

- Type 1: Can be traversed by Alice only.
- Type 2: Can be traversed by Bob only.
- Type 3: Can be traversed by both Alice and Bob.
Given an array edges where edges[i] = [typei, ui, vi] represents a bidirectional edge of type typei between nodes ui and vi, find the maximum number of edges you can remove so that after removing the edges, the graph can still be fully traversed by both Alice and Bob. The graph is fully traversed by Alice and Bob if starting from any node, they can reach all other nodes.

Return the maximum number of edges you can remove, or return -1 if Alice and Bob cannot fully traverse the graph.

### 解题思路

对alice和bob分别维护两个并查集，类似于克鲁斯卡尔算法，先加3类边，再分别加1、2类边，求出最少需要加入多少条边

### 代码
```python
class UF:
    def __init__(self, n):
        self.rank = {}
        self.parent = {i: i for i in range(n + 1)}
        self.com = n
    
    def find(self, v):
        if self.parent[v] != v:
            self.parent[v] = self.find(self.parent[v])
        return self.parent[v]
    
    def union(self, v1, v2):
        p1 = self.find(v1)
        p2 = self.find(v2)
        if p1 not in self.rank:
            self.rank[p1] = 0
        if p2 not in self.rank:
            self.rank[p2] = 0
        if p1 != p2:
            if self.rank[p1] > self.rank[p2]:
                self.parent[p2] = p1
            else:
                self.parent[p1] = p2
                if self.rank[p1] == self.rank[p2]:
                    self.rank[p2] += 1
            self.com -= 1
            return True
        return False
    
    def is_connect(self):
        return self.com == 1

class Solution:
    def maxNumEdgesToRemove(self, n: int, edges: List[List[int]]) -> int:
        Alice, Bob = UF(n), UF(n)
        res = 0
        for t, x, y in edges:
            if t == 3:
                res += Alice.union(x, y) and Bob.union(x, y)
        for t, x, y in edges:
            if t == 1:
                res += Alice.union(x, y)
            elif t == 2:
                res += Bob.union(x, y)
        return len(edges) - res if Alice.is_connect() and Bob.is_connect() else -1
```
