---
layout:     post
title:      LeetCode 973 K Closest Points to Origin (Python)
number:     973
level:      Medium
lcurl:      k-closest-points-to-origin
youtube:    UcGlcA1NE-U
bilibili1:  //player.bilibili.com/player.html?aid=285825706&bvid=BV1Vf4y1278J&cid=196765486&page=1
xigua:      
date:       2020-05-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Priority Queue
---

### 题目

We have a list of points on the plane.  Find the K closest points to the origin (0, 0).

(Here, the distance between two points on a plane is the Euclidean distance.)

You may return the answer in any order.  The answer is guaranteed to be unique (except for the order that it is in.)

### 解题思路

1. 对所有点按距离排序，取k个最小的
2. 维护一个长度为k的优先队列，当队满了之后，对于每个新加入的距离，在push进队列之后，再把最远的pop出来

### 代码
```python
class Solution:
    def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
        q = []
        for px, py in points:
            t = (-px * px - py * py, px, py)
            if len(q) < K:
                heapq.heappush(q, t)
            else:
                heapq.heappushpop(q, t)
        return [[p[1], p[2]] for p in q]
```
