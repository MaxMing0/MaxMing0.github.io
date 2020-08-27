---
layout:     post
title:      LeetCode 436 Find Right Interval (Python)
number:     436
level:      Medium
lcurl:      find-right-interval
youtube:    fEVyHmO-KF8
bilibili1:  //player.bilibili.com/player.html?aid=926971747&bvid=BV1YT4y1w7EP&cid=229456580&page=1
xigua:      
date:       2020-08-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given a set of intervals, for each of the interval i, check if there exists an interval j whose start point is bigger than or equal to the end point of the interval i, which can be called that j is on the "right" of i.

For any interval i, you need to store the minimum interval j's index, which means that the interval j has the minimum start point to build the "right" relationship for interval i. If the interval j doesn't exist, store -1 for the interval i. Finally, you need output the stored value of each interval as an array.

Note:

- You may assume the interval's end point is always bigger than its start point.
- You may assume none of these intervals have the same start point.

### 解题思路

对所有区间按照开始位置，以及index进行排序，之后对每个区间进行二分，找到第一个比右端点大的区间，把结果放到对应位置

### 代码
```python
class Solution:
    def findRightInterval(self, intervals: List[List[int]]) -> List[int]:
        intervals = sorted((e[0], i, e[1]) for i, e in enumerate(intervals))
        l = len(intervals)
        res = [0] * l
        for e in intervals:
            r = bisect.bisect_left(intervals, (e[2], ))
            res[e[1]] = intervals[r][1] if r < l else -1
        return res
```
