---
layout:     post
title:      LeetCode 1453 Maximum Number of Darts Inside of a Circular Dartboard (Python)
number:     1453
level:      Hard
lcurl:      maximum-number-of-darts-inside-of-a-circular-dartboard
youtube:    A3Xs-ZeZ1vs
bilibili1:  //player.bilibili.com/player.html?aid=625728665&bvid=BV1Ut4y117jp&cid=192315687&page=1
xigua:      
date:       2020-05-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Geometry
---

### 题目

You have a very large square wall and a circular dartboard placed on the wall. You have been challenged to throw darts into the board blindfolded. Darts thrown at the wall are represented as an array of points on a 2D plane. 

Return the maximum number of points that are within or lie on any circular dartboard of radius r.

### 解题思路

第一种四次方的做法：枚举三个点，求出用这三个点确定的圆心，判断所有的点距离这个点是否小于r，求出可以覆盖点的个数

第二种三次方的做饭：枚举两个点，用两个点和半径，确定圆心，之后做与第一种方法相同的操作，求出可以覆盖的点的个数

### 代码
```python
class Solution:
    def numPoints(self, points: List[List[int]], r: int) -> int:
        res = 1
        for (x1, y1), (x2, y2) in itertools.combinations(points, 2):
            d = (x2 - x1) ** 2 + (y2 - y1) ** 2
            if d > 4 * r ** 2 or d == 0:
                continue
            
            x0 = (x1 + x2) / 2.0 + (y2 - y1) * (r * r - d / 4) ** 0.5 / d ** 0.5
            y0 = (y1 + y2) / 2.0 - (x2 - x1) * (r * r - d / 4) ** 0.5 / d ** 0.5
            res = max(res, sum((x - x0) ** 2 + (y - y0) ** 2 <= r * r + 0.00001 for x, y in points))
            
            x0 = (x1 + x2) / 2.0 - (y2 - y1) * (r * r - d / 4) ** 0.5
            y0 = (y1 + y2) / 2.0 + (x2 - x1) * (r * r - d / 4) ** 0.5
            res = max(res, sum((x - x0) ** 2 + (y - y0) ** 2 <= r * r + 0.00001 for x, y in points))
        return res
```
