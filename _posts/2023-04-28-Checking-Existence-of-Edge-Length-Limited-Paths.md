---
layout:     post
title:      LeetCode 1697 Checking Existence of Edge Length Limited Paths (Python)
number:     1697
level:      Hard
lcurl:      checking-existence-of-edge-length-limited-paths
youtube:    rUuwk_3MelI
bilibili1:  
xigua:      
date:       2023-04-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
---

### 题目

An undirected graph of n nodes is defined by edgeList, where edgeList[i] = [ui, vi, disi] denotes an edge between nodes ui and vi with distance disi. Note that there may be multiple edges between two nodes.

Given an array queries, where queries[j] = [pj, qj, limitj], your task is to determine for each queries[j] whether there is a path between pj and qj such that each edge on the path has a distance strictly less than limitj .

Return a boolean array answer, where answer.length == queries.length and the jth value of answer is true if there is a path for queries[j] is true, and false otherwise.

### 解题思路

把边和query按照权和limit从小到大排序，维护一个并查集，处理当前query时，把所有权小于limit的边所链接的点加入到并查集里，判断查询的两个点是否处于一个集合里

### 代码
```python
class Solution:
    def distanceLimitedPathsExist(self, n: int, edgeList: List[List[int]], queries: List[List[int]]) -> List[bool]:
        def find(v):
            if parent[v] != v:
                parent[v] = find(parent[v])
            return parent[v]

        def union(x, y):
            p1 = find(x)
            p2 = find(y)
            if p1 not in rank:
                rank[p1] = 0
            if p2 not in rank:
                rank[p2] = 0
            if p1 != p2:
                if rank[p1] > rank[p2]:
                    parent[p2] = p1
                else:
                    parent[p1] = p2
                    if rank[p1] == rank[p2]:
                        rank[p2] += 1

        rank = {}
        parent = {i: i for i in range(n)}
        m = len(queries)
        res = [False] * m
        queries = sorted([[i] + queries[i] for i in range(m)], key=lambda x:x[3])
        edgeList = sorted(edgeList, key=lambda x:x[2])
        j = 0
        for i, x, y, limit in queries:
            while j < len(edgeList) and edgeList[j][2] < limit:
                union(edgeList[j][0], edgeList[j][1])
                j += 1
            res[i] = find(x) == find(y)
        return res
```
