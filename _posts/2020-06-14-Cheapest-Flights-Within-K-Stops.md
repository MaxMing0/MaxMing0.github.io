---
layout:     post
title:      LeetCode 787 Cheapest Flights Within K Stops (Python)
number:     787
level:      Medium
lcurl:      cheapest-flights-within-k-stops
youtube:    xKUf_51tC3U
bilibili1:  //player.bilibili.com/player.html?aid=371103820&bvid=BV1DZ4y1H7oH&cid=202152895&page=1
xigua:      
date:       2020-06-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

There are n cities connected by m flights. Each flight starts from city u and arrives at v with a price w.

Now given all the cities and flights, together with starting city src and the destination dst, your task is to find the cheapest price from src to dst with up to k stops. If there is no such route, output -1.

Constraints:

- The number of nodes n will be in range [1, 100], with nodes labeled from 0 to n - 1.
- The size of flights will be in range [0, n * (n - 1) / 2].
- The format of each flight will be (src, dst, price).
- The price of each flight will be in the range [1, 10000].
- k is in the range of [0, n - 1].
- There will not be any duplicated flights or self cycles.

### 解题思路

使用Dijkstra+Heap求单源最短路，这里不同的地方是，需要记录到每个点转机数，如果已经超过限制，就不能进行更新

### 代码
```python
from collections import defaultdict
import heapq
class Solution:
    def findCheapestPrice(self, n: int, flights: List[List[int]], src: int, dst: int, K: int) -> int:
        edge = defaultdict(list)
        for u, v, w in flights:
            edge[u].append((v, w))
        dist = {}
        q = [(0, src, 0)]
        while q:
            cost, cur, k = heapq.heappop(q)
            if k > K + 1 or cost > dist.get((cur, k), float('inf')):
                continue
            if cur == dst:
                return cost
            for node, w in edge[cur]:
                tmp = cost + w
                if tmp < dist.get((node, k + 1), float('inf')):
                    heapq.heappush(q, (tmp, node, k + 1))
                    dist[(node, k + 1)] = tmp
        return -1
```
