---
layout:     post
title:      LeetCode 2477 Minimum Fuel Cost to Report to the Capital (Python)
number:     2477
level:      Medium
lcurl:      minimum-fuel-cost-to-report-to-the-capital
youtube:    OURD4k15cOs
bilibili1:  
xigua:      
date:       2023-02-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
    - Graph
    - Tree
---

### 题目

There is a tree (i.e., a connected, undirected graph with no cycles) structure country network consisting of n cities numbered from 0 to n - 1 and exactly n - 1 roads. The capital city is city 0. You are given a 2D integer array roads where roads[i] = [ai, bi] denotes that there exists a bidirectional road connecting cities ai and bi.

There is a meeting for the representatives of each city. The meeting is in the capital city.

There is a car in each city. You are given an integer seats that indicates the number of seats in each car.

A representative can use the car in their city to travel or change the car and ride with another representative. The cost of traveling between two cities is one liter of fuel.

Return the minimum number of liters of fuel to reach the capital city.

### 解题思路

贪心，每次从叶节点（度为1）开始遍历，把所有人送到下一个城市（花费`ceil(people/seats)`），把花费的油加到结果里，直到所有人都到达首都

### 代码
```python
from collections import defaultdict
class Solution:
    def minimumFuelCost(self, roads: List[List[int]], seats: int) -> int:
        degree = [0] * (len(roads) + 1)
        edge = defaultdict(list)
        for x, y in roads:
            degree[x] += 1
            degree[y] += 1
            edge[x].append(y)
            edge[y].append(x)
        
        s = []
        for i, n in enumerate(degree[1:]):
            if n == 1:
                s.append(i + 1)
        res = 0
        people = [1] * (len(roads) + 1)
        while s:
            cur = s.pop()
            res += math.ceil(people[cur] / seats)
            for n in edge[cur]:
                degree[n] -= 1
                people[n] += people[cur]
                if degree[n] == 1 and n != 0:
                    s.append(n)
        return res
```
