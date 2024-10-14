---
layout:     post
title:      LeetCode 2421 Number of Good Paths (Python)
number:     2421
level:      Hard
lcurl:      
youtube:    
bilibili1:  
xigua:      
date:       
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
    - DFS
---

### 题目

There is a tree (i.e. a connected, undirected graph with no cycles) consisting of n nodes numbered from 0 to n - 1 and exactly n - 1 edges.

You are given a 0-indexed integer array vals of length n where vals[i] denotes the value of the ith node. You are also given a 2D integer array edges where edges[i] = [ai, bi] denotes that there exists an undirected edge connecting nodes ai and bi.

A good path is a simple path that satisfies the following conditions:

The starting node and the ending node have the same value.
All nodes between the starting node and the ending node have values less than or equal to the starting node (i.e. the starting node's value should be the maximum value along the path).
Return the number of distinct good paths.

Note that a path and its reverse are counted as the same path. For example, 0 -> 1 is considered to be the same as 1 -> 0. A single node is also considered as a valid path.

### 解题思路

按照每个点的值从大到小排序，进行若干轮dfs，每一轮对值相同的每个点进行dfs，每次只能走到比当前轮小的节点

不是用dfs，可以用union find来维护，每次把当前值的点加入，求出一个有多少个集合，每个集合中任两个当前值的点可以构成一条道路

### 代码
```python
# TLE without UF
class Solution:
    def numberOfGoodPaths(self, vals: List[int], edges: List[List[int]]) -> int:
        e = defaultdict(list)
        for x, y in edges:
            e[x].append(y)
            e[y].append(x)
        rev = defaultdict(set)
        for i, v in enumerate(vals):
            rev[v].add(i)
        res = 0
        for v in sorted(rev.keys(), reverse=True):
            for n in rev[v]:
                s = [n]
                visited = {n}
                while s:
                    cur = s.pop()
                    for nei in e[cur]:
                        if nei in visited or vals[nei] > v:
                            continue
                        s.append(nei)
                        visited.add(nei)
                        if vals[nei] == v:
                            res += 1
        return res // 2 + len(vals)
```
