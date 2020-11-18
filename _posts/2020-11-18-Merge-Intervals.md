---
layout:     post
title:      LeetCode 56 Merge Intervals (Python)
number:     56
level:      Medium
lcurl:      merge-intervals
youtube:    V_RgvDhJL-8
bilibili1:  //player.bilibili.com/player.html?aid=415307811&bvid=BV1pV411a7t4&cid=257139700&page=1
xigua:      
date:       2020-11-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

### 解题思路

按区间开始位置进行排序，遍历所有区间，判断当前区间是否能和最后一个区间合并

### 代码
```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda x: x[0])
        res = [intervals[0]]
        for interval in intervals[1:]:
            if res[-1][1] >= interval[0]:
                res[-1][1] = max(interval[1], res[-1][1])
            else:
                res.append(interval)
        return res
```
