---
layout:     post
title:      LeetCode 452 Minimum Number of Arrows to Burst Balloons (Python)
number:     452
level:      Medium
lcurl:      minimum-number-of-arrows-to-burst-balloons
youtube:    NiFlouOlds4
bilibili1:  //player.bilibili.com/player.html?aid=372429337&bvid=BV1PZ4y1L7VM&cid=244215174&page=1
xigua:      
date:       2020-10-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

There are some spherical balloons spread in two-dimensional space. For each balloon, provided input is the start and end coordinates of the horizontal diameter. Since it's horizontal, y-coordinates don't matter, and hence the x-coordinates of start and end of the diameter suffice. The start is always smaller than the end.

An arrow can be shot up exactly vertically from different points along the x-axis. A balloon with xstart and xend bursts by an arrow shot at x if xstart ≤ x ≤ xend. There is no limit to the number of arrows that can be shot. An arrow once shot keeps traveling up infinitely.

Given an array points where points[i] = [xstart, xend], return the minimum number of arrows that must be shot to burst all balloons.

### 解题思路

贪心，先把气球按结束位置从小到大排序，每次都从当前气球的最右端射箭

### 代码
```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        if not points:
            return 0
        points.sort(key=lambda x: x[1])
        res = 1
        cur = points[0][1]
        for p in points[1:]:
            if cur < p[0]:
                res += 1
                cur = p[1]
        return res
```
