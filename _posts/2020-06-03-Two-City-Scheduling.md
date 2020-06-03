---
layout:     post
title:      LeetCode 1029 Two City Scheduling (Python)
number:     1029
level:      Easy
lcurl:      https://leetcode.com/problems/two-city-scheduling
youtube:    _IZ1pPdVqdQ
bilibili1:  //player.bilibili.com/player.html?aid=840947562&bvid=BV1t54y1Q7G8&cid=198226709&page=1
xigua:      
date:       2020-06-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

There are 2N people a company is planning to interview. The cost of flying the i-th person to city A is costs[i][0], and the cost of flying the i-th person to city B is costs[i][1].

Return the minimum cost to fly every person to a city such that exactly N people arrive in each city.

### 解题思路

先让所有人去A城市，让第i个人去B城市的额外花销是`costs[i][1] - costs[i][0]`，使用优先队列找出额外花销最小的n个人，让他们去B城市

### 代码
```python
import heapq
class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        n = len(costs) // 2
        res = 0
        q = []
        for i in range(n):
            res += costs[i][0]
            heapq.heappush(q, costs[i][1] - costs[i][0])
        for i in range(n, 2 * n):
            res += costs[i][0]
            res += heapq.heappushpop(q, costs[i][1] - costs[i][0])
        return res
```
