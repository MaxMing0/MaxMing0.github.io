---
layout:     post
title:      LeetCode 949 Largest Time for Given Digits (Python)
number:     949
level:      Easy
lcurl:      largest-time-for-given-digits
youtube:    nFXU2p3ehzQ
bilibili1:  //player.bilibili.com/player.html?aid=244448459&bvid=BV13v41117QS&cid=231219667&page=1
xigua:      
date:       2020-09-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an array of 4 digits, return the largest 24 hour time that can be made.

The smallest 24 hour time is 00:00, and the largest is 23:59.  Starting from 00:00, a time is larger if more time has elapsed since midnight.

Return the answer as a string of length 5.  If no valid time can be made, return an empty string.

### 解题思路

枚举四个数的排列，找到符合条件的最大时间

### 代码
```python
class Solution:
    def largestTimeFromDigits(self, A: List[int]) -> str:
        res = -1
        for h1, h2, m1, m2 in itertools.permutations(A):
            hour = h1 * 10 + h2
            minute = m1 * 10 + m2
            if hour < 24 and minute < 60:
                time = hour * 60 + minute
                res = max(res, time)
        return "%02d:%02d" % divmod(res, 60) if res >= 0 else ""
```
