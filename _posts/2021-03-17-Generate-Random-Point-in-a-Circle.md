---
layout:     post
title:      LeetCode 478 Generate Random Point in a Circle (Python)
number:     478
level:      Medium
lcurl:      generate-random-point-in-a-circle
youtube:    uBWYS_Hc4IM
bilibili1:  //player.bilibili.com/player.html?aid=587176309&bvid=BV1Nz4y127a1&cid=311517746&page=1
xigua:      
date:       2021-03-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given the radius and x-y positions of the center of a circle, write a function randPoint which generates a uniform random point in the circle.

Note:

1. input and output values are in floating-point.
2. radius and x-y position of the center of the circle is passed into the class constructor.
3. a point on the circumference of the circle is considered to be in the circle.
4. randPoint returns a size 2 array containing x-position and y-position of the random point, in that order.

### 解题思路

拒绝采样，随机-1到1直接的一个点，如果在单位元范围内，进行缩放和平移对应到要求的点，不在则继续随机

### 代码
```python
class Solution:
    def __init__(self, radius: float, x_center: float, y_center: float):
        self.r = radius
        self.x = x_center
        self.y = y_center

    def randPoint(self) -> List[float]:
        while True:
            u = 2 * random.random() - 1
            v = 2 * random.random() - 1
            if u * u + v * v <= 1:
                return [self.x + u * self.r, self.y + v * self.r]
```
