---
layout:     post
title:      LeetCode 547 Number of Provinces (Python)
number:     547
level:      Medium
lcurl:      number-of-provinces
youtube:    lIxyApM4mBA
bilibili1:  
xigua:      
date:       2022-02-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.

A province is a group of directly or indirectly connected cities and no other cities outside of the group.

You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise.

Return the total number of provinces.

### 解题思路

题目相当于求无向图连通分量个数

### 代码
```python
class Solution:
    def findCircleNum(self, isConnected: List[List[int]]) -> int:
        n = len(isConnected)
        res = 0
        visit = set()
        for i in range(n):
            if i in visit:
                continue
            s = [i]
            visit.add(i)
            res += 1
            while s:
                cur = s.pop()
                for j in range(n):
                    if j not in visit and isConnected[cur][j] == 1:
                        s.append(j)
                        visit.add(j)
        return res
```
