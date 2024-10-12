---
layout:     post
title:      LeetCode 84 Largest Rectangle in Histogram (Python)
number:     84
level:      Hard
lcurl:      largest-rectangle-in-histogram
youtube:    
bilibili1:  
xigua:      
date:       2024-10-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

### 解题思路

维护一个单调栈，保持高度不降（栈里存高度的下标，为了计算矩形宽度），如果当前高度小于栈顶高度，则从栈顶开始计算向左可以构成的最大矩形，知道当前高度大于等于栈顶高度

### 代码
```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        heights.append(0)
        res, stack = 0, []
        for i, height in enumerate(heights):
            while stack and heights[stack[-1]] > height:
                ind = stack.pop()
                width = i - 1 - (stack[-1] if stack else -1)
                res = max(res, width * heights[ind])
            stack.append(i)
        return res
```
