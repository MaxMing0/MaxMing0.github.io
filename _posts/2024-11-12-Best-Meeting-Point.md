---
layout:     post
title:      LeetCode 296 Best Meeting Point (Python)
number:     296
level:      Hard
lcurl:      best-meeting-point
youtube:    
bilibili1:  
xigua:      
date:       2024-11-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an m x n binary grid grid where each 1 marks the home of one friend, return the minimal total travel distance.

The total travel distance is the sum of the distances between the houses of the friends and the meeting point.

The distance is calculated using Manhattan Distance, where distance(p1, p2) = |p2.x - p1.x| + |p2.y - p1.y|.

### 解题思路

分开考虑行和列，对于行或者列，从小到大找到所有位置，相遇点应该在中位数，计算到每个点的距离

### 代码
```python
class Solution:
    def minTotalDistance(self, grid: List[List[int]]) -> int:
        def dist(points, x):
            ret = 0
            for point in points:
                ret += abs(point - x)
            return ret

        rows, cols = [], []
        for row in range(len(grid)):
            for col in range(len(grid[0])):
                if grid[row][col]:
                    rows.append(row)
        for col in range(len(grid[0])):
            for row in range(len(grid)):
                if grid[row][col]:
                    cols.append(col)
        return dist(rows, rows[len(rows) // 2]) + dist(cols, cols[len(cols) // 2])
```
