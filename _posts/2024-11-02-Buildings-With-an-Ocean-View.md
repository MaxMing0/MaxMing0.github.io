---
layout:     post
title:      LeetCode 1762 Buildings With an Ocean View (Python)
number:     1762
level:      Medium
lcurl:      buildings-with-an-ocean-view
youtube:    
bilibili1:  
xigua:      
date:       2024-11-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

There are n buildings in a line. You are given an integer array heights of size n that represents the heights of the buildings in the line.

The ocean is to the right of the buildings. A building has an ocean view if the building can see the ocean without obstructions. Formally, a building has an ocean view if all the buildings to its right have a smaller height.

Return a list of indices (0-indexed) of buildings that have an ocean view, sorted in increasing order.

### 解题思路

最右边一定可以看到海加入到结果中，从最右边向前遍历数组，如果当前楼的高度大于结果中最后一个，则加到结果中

### 代码
```python
class Solution:
    def findBuildings(self, heights: List[int]) -> List[int]:
        n = len(heights)
        res = [n - 1]
        for i in range(n - 2, -1, -1):
            if heights[i] > heights[res[-1]]:
                res.append(i)
        return res[::-1]
```
