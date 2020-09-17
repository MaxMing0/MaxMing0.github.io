---
layout:     post
title:      LeetCode 1041 Robot Bounded In Circle (Python)
number:     1041
level:      Medium
lcurl:      robot-bounded-in-circle
youtube:    i3Alr_FNu_c
bilibili1:  //player.bilibili.com/player.html?aid=754597260&bvid=BV1dk4y1y7RH&cid=236189826&page=1
xigua:      
date:       2020-09-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

On an infinite plane, a robot initially stands at (0, 0) and faces north.  The robot can receive one of three instructions:

- "G": go straight 1 unit;
- "L": turn 90 degrees to the left;
- "R": turn 90 degress to the right.
The robot performs the instructions given in order, and repeats them forever.

Return true if and only if there exists a circle in the plane such that the robot never leaves the circle.

### 解题思路

经过一系列的操作，主要回到原点，或者朝向与最开始不同，就可以形成一个圈

### 代码
```python
class Solution:
    def isRobotBounded(self, instructions: str) -> bool:
        x = y = 0
        d = (0, 1)
        for c in instructions:
            if c == 'G':
                x, y = x + d[0], y + d[1]
            elif c =='L':
                d = (-d[1], d[0])
            else:
                d = (d[1], -d[0])
        return (x == 0 and y == 0) or d != (0, 1)
```
