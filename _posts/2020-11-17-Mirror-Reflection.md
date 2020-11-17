---
layout:     post
title:      LeetCode 858 Mirror Reflection (Python)
number:     858
level:      Medium
lcurl:      mirror-reflection
youtube:    ADLTKkx0P0w
bilibili1:  
xigua:      
date:       2020-11-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

There is a special square room with mirrors on each of the four walls.  Except for the southwest corner, there are receptors on each of the remaining corners, numbered 0, 1, and 2.

The square room has walls of length p, and a laser ray from the southwest corner first meets the east wall at a distance q from the 0th receptor.

Return the number of the receptor that the ray meets first.  (It is guaranteed that the ray will meet a receptor eventually.)

### 解题思路

将题目转换成光线一直沿直线传播，镜像接收器的位置

### 代码
```python
class Solution:
    def mirrorReflection(self, p: int, q: int) -> int:
        from fractions import gcd
        g = gcd(p, q)
        if (p // g) % 2 == 0:
            return 2
        return (q // g) % 2
```
