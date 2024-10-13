---
layout:     post
title:      LeetCode 539 Minimum Time Difference (Python)
number:     539
level:      Medium
lcurl:      minimum-time-difference
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

Given a list of 24-hour clock time points in "HH:MM" format, return the minimum minutes difference between any two time-points in the list.

### 解题思路

创建一个60*24的布尔数组表示每分钟，把对应的时间标为True，如果出现重复则结果为0

扫描这个数组，记录前一个、第一个和最后一个时间，然后当前时间和前一个得到最小值。最后单独处理第一个和最后一个时间

### 代码
```python
class Solution:
    def findMinDifference(self, timePoints: List[str]) -> int:
        M = 60 * 24
        bucket = [False for _ in range(M)]
        for timepoint in timePoints:
            h, m = map(int, timepoint.split(":"))
            t = h * 60 + m
            if bucket[t]:
                return 0
            bucket[t] = True
        first = last = prev = -1
        res = M
        for i in range(M):
            if bucket[i]:
                last = i
                if first == -1:
                    first = i
                else:
                    res = min(res, last - prev)
                prev = i
        return min(res, first + M - last)
```
