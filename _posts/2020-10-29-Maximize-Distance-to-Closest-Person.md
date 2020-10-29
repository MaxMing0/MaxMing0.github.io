---
layout:     post
title:      LeetCode 849 Maximize Distance to Closest Person (Python)
number:     849
level:      Medium
lcurl:      maximize-distance-to-closest-person
youtube:    tTCwz83mLX0
bilibili1:  //player.bilibili.com/player.html?aid=372517966&bvid=BV1ZZ4y1G7iT&cid=250617421&page=1
xigua:      
date:       2020-10-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an array representing a row of seats where seats[i] = 1 represents a person sitting in the ith seat, and seats[i] = 0 represents that the ith seat is empty (0-indexed).

There is at least one empty seat, and at least one person sitting.

Alex wants to sit in the seat such that the distance between him and the closest person to him is maximized. 

Return that maximum distance to the closest person.

### 解题思路

数最多连续0的个数(n)，那么答案为(n + 1) / 2，单独处理两端

### 代码
```python
class Solution:
    def maxDistToClosest(self, seats: List[int]) -> int:
        cur, n = 0, len(seats)
        for k in range(n):
            if seats[k]:
                break
            else:
                cur += 1
        res = cur
        zeros = cur = 0
        for i in range(k, n):
            if seats[i]:
                zeros = max(zeros, cur)
                cur = 0
            else:
                cur += 1
        res = max(res, (zeros + 1) // 2, cur)
        return res
```
