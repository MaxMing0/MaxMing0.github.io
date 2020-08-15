---
layout:     post
title:      LeetCode 435 Non-overlapping Intervals (Python)
number:     435
level:      Medium
lcurl:      non-overlapping-intervals
youtube:    WOYG4yGtnd0
bilibili1:  //player.bilibili.com/player.html?aid=754184288&bvid=BV1Ak4y1U7f8&cid=224707611&page=1
xigua:      
date:       2020-08-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Given a collection of intervals, find the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

### 解题思路

贪心，先按区间左端点排序，遍历区间，如果遇到重叠的区间，留右端点小的

### 代码
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        if len(intervals) == 0:
            return 0
        intervals.sort()
        now = intervals[0][1]
        res = 0
        for i in intervals[1:]:
            if i[0] < now:
                now = min(i[1], now)
                res += 1
            else:
                now = i[1]
        return res
```
