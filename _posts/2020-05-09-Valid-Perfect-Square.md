---
layout:     post
title:      LeetCode 367 Valid Perfect Square (Python)
number:     367
level:      easy
lcurl:      valid-perfect-square
youtube:    TqiXE_MicWw
bilibili1:  
xigua:      
date:       2020-05-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
    - Math
---

### 题目

Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as `sqrt`.

### 解题思路

二分搜索n，使得num = n * n

### 代码
```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        l, r = 0, num
        while l <= r:
            m = (l + r) // 2
            t = m * m
            if t == num:
                return True
            if t < num:
                l = m + 1
            else:
                r = m - 1
        return False
```
