---
layout:     post
title:      LeetCode 1466 Reorder Routes to Make All Paths Lead to the City Zero (Python)
number:     1466
level:      Medium
lcurl:      reorder-routes-to-make-all-paths-lead-to-the-city-zero
youtube:    aS2qXbxCLQU
bilibili1:  
xigua:      
date:       2023-03-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
    - DFS
---

### 题目

There are n cities numbered from 0 to n - 1 and n - 1 roads such that there is only one way to travel between two different cities (this network form a tree). Last year, The ministry of transport decided to orient the roads in one direction because they are too narrow.

Roads are represented by connections where connections[i] = [ai, bi] represents a road from city ai to city bi.

This year, there will be a big event in the capital (city 0), and many people want to travel to this city.

Your task consists of reorienting some roads such that each city can visit the city 0. Return the minimum number of edges changed.

It's guaranteed that each city can reach city 0 after reorder.

### 解题思路

把所有边的反向边加到图中，从0开始进行遍历，在遍历的时候如果走的是原有的边，则这个边需要被翻转

### 代码
```python
class Solution:
    def minReorder(self, n: int, connections: List[List[int]]) -> int:
        edge = defaultdict(list)
        for x, y in connections:
            edge[x].append((y, 1))
            edge[y].append((x, 0))
        res = 0
        s = [(0, -1)]
        while s:
            cur, parent = s.pop()
            for nei, direction in edge[cur]:
                if nei != parent:
                    res += direction
                    s.append((nei, cur))
        return res
```
