---
layout:     post
title:      LeetCode 1232 Check If It Is a Straight Line (Python)
number:     1232
level:      Easy
lcurl:      check-if-it-is-a-straight-line
youtube:    fiuEeBWYFJM
bilibili1:  //player.bilibili.com/player.html?aid=370590454&bvid=BV14Z4y1s74c&cid=188570218&page=1
xigua:      
date:       2020-05-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
    - Geometry
---

### 题目

You are given an array coordinates, coordinates[i] = [x, y], where [x, y] represents the coordinate of a point. Check if these points make a straight line in the XY plane.

### 解题思路

取前两点，求斜率，然后用后面的每个点和第一个点求斜率，如果所有的斜率都相同，则所有点共线，并不需要把斜率求出来，只需要记录y轴和x轴的差，相乘就可以了

### 代码
```python
class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        dy = coordinates[1][1] - coordinates[0][1]
        dx = coordinates[1][0] - coordinates[0][0]
        for i in range(2, len(coordinates)):
            dyp = coordinates[i][1] - coordinates[0][1]
            dxp = coordinates[i][0] - coordinates[0][0]
            if dy * dxp != dx * dyp:
                return False
        return True
```
