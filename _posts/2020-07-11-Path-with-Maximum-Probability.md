---
layout:     post
title:      LeetCode 1514 Path with Maximum Probability (Python)
number:     1514
level:      Medium
lcurl:      path-with-maximum-probability
youtube:    84QiHUkGPtg
bilibili1:  //player.bilibili.com/player.html?aid=753776844&bvid=BV1Ak4y1B7yR&cid=211627490&page=1
xigua:      
date:       2020-07-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

You are given an undirected weighted graph of n nodes (0-indexed), represented by an edge list where edges[i] = [a, b] is an undirected edge connecting the nodes a and b with a probability of success of traversing that edge succProb[i].

Given two nodes start and end, find the path with the maximum probability of success to go from start to end and return its success probability.

If there is no path from start to end, return 0. Your answer will be accepted if it differs from the correct answer by at most 1e-5.

### 解题思路

使用Dijkstra求最长路，区别是把距离的相加变成相乘

### 代码
```python
class Solution:
    def maxProbability(self, n: int, edges: List[List[int]], succProb: List[float], start: int, end: int) -> float:
        maps = defaultdict(list)
        for i in range(len(edges)):
            maps[edges[i][0]].append((edges[i][1], succProb[i]))
            maps[edges[i][1]].append((edges[i][0], succProb[i]))
        q = [(-1, start)]
        dist = defaultdict(float)
        dist[start] = -1
        while q:
            curdist, cur = heapq.heappop(q)
            if cur == end:
                return -curdist
            for node, prob in maps[cur]:
                tmp = curdist * prob
                if tmp < dist[node]:
                    dist[node] = tmp
                    heapq.heappush(q, (tmp, node))
        return 0
```
