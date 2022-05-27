---
layout:     post
title:      LeetCode 743 Network Delay Time (Python)
number:     743
level:      Medium
lcurl:      network-delay-time
youtube:    FVMqnbUi0_M
bilibili1:  
xigua:      
date:       2022-05-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

You are given a network of n nodes, labeled from 1 to n. You are also given times, a list of travel times as directed edges times[i] = (ui, vi, wi), where ui is the source node, vi is the target node, and wi is the time it takes for a signal to travel from source to target.

We will send a signal from a given node k. Return the minimum time it takes for all the n nodes to receive the signal. If it is impossible for all the n nodes to receive the signal, return -1.

### 解题思路

使用Dijkstra求距离起点最远的距离

### 代码
```python
class Solution:
    def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
        edge = defaultdict(list)
        for u, v, w in times:
            edge[u].append((v, w))
        q = [(0, k)]
        visit = set()
        while q:
            curdist, u = heapq.heappop(q)
            if u in visit:
                continue
            visit.add(u)
            if len(visit) == n:
                return curdist
            for v, w in edge[u]:
                heapq.heappush(q, (curdist + w, v))
        return -1
```
