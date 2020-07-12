---
layout:     post
title:      LeetCode LeetCode 1515 Best Position for a Service Centre (Python)
number:     1515
level:      Hard
lcurl:      best-position-for-a-service-centre
youtube:    8IX9j5WLLD4
bilibili1:  //player.bilibili.com/player.html?aid=328828637&bvid=BV1UA411e7PC&cid=211645831&page=1
xigua:      
date:       2020-07-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

A delivery company wants to build a new service centre in a new city. The company knows the positions of all the customers in this city on a 2D-Map and wants to build the new centre in a position such that the sum of the euclidean distances to all customers is minimum.

Given an array positions where positions[i] = [xi, yi] is the position of the ith customer on the map, return the minimum sum of the euclidean distances to all customers.

In other words, you need to choose the position of the service centre [xcentre, ycentre] such that the following formula is minimized:

Answers within 10^-5 of the actual value will be accepted.

### 解题思路

如果把结果的x y坐标为xy轴，距离所有点距离之和为z轴，那么图像一定存在一个最小值，而且不存在局部最小值

求最小值的方法是先从任意一点开始，以一个步长向四周移动，如果存在一个更小的值，则移动到这个点，否则缩小步长，直到步长小于精度

### 代码
```python
class Solution:
    def getMinDistSum(self, positions: List[List[int]]) -> float:
        def dist(a, b):
            res = 0
            for x, y in positions:
                res += math.sqrt((x-a)**2 + (y-b)**2)
            return res
        
        step = 1
        n = len(positions)
        curx = cury = 0
        for x, y in positions:
            curx += x
            cury += y
        curx /= n
        cury /= n
        curdist = dist(curx, cury)
        while step > 0.000001:
            f = True
            for dirx, diry in [(0, step), (0, -step), (step, 0), (-step, 0)]:
                tx, ty = curx + dirx, cury + diry
                tmp = dist(tx, ty)
                if tmp < curdist:
                    curdist = tmp
                    curx, cury = tx, ty
                    f = False
            if f:
                step /= 10
        return curdist
```
