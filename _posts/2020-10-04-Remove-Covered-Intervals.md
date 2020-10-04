---
layout:     post
title:      LeetCode 1288 Remove Covered Intervals (Python)
number:     1288
level:      Medium
lcurl:      remove-covered-intervals
youtube:    TwUw7Sv6378
bilibili1:  //player.bilibili.com/player.html?aid=457339138&bvid=BV165411j7S8&cid=242036827&page=1
xigua:      
date:       2020-10-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Given a list of intervals, remove all intervals that are covered by another interval in the list.

Interval [a,b) is covered by interval [c,d) if and only if c <= a and b <= d.

After doing so, return the number of remaining intervals.

### 解题思路

先对所有区间进行排序，左端点从小到大，右端点从大到小，然后遍历每个区间，如果新的区间不被之前的包含，结果+1

### 代码
```python
class Solution:
    def removeCoveredIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort(key = lambda x: (x[0], -x[1]))
        res = prev = 0
        for _, r in intervals:
            if r > prev:
                res += 1    
                prev = r
        return res
```
