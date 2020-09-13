---
layout:     post
title:      LeetCode 57 Insert Interval (Python)
number:     57
level:      Hard
lcurl:      insert-interval
youtube:    MELs_LUsFDs
bilibili1:  //player.bilibili.com/player.html?aid=669595673&bvid=BV1Ja4y1j7cG&cid=234961377&page=1
xigua:      
date:       2020-09-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.

### 解题思路

分三个部分，先把在newInterval前面的区间加到结果里，再把与newInterval相交的区间进行合并，最后把余下的区间加到结果里

### 代码
```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        n = len(intervals)
        if n == 0:
            return [newInterval]
        res = []
        i = 0
        while i < n and intervals[i][1] < newInterval[0]:
            res.append(intervals[i])
            i += 1
        l, r = newInterval
        while i < n and intervals[i][0] <= newInterval[1]:
            l = min(l, intervals[i][0])
            r = max(r, intervals[i][1])
            i += 1
        res.append([l, r])
        res.extend(intervals[i:])
        return res
```
