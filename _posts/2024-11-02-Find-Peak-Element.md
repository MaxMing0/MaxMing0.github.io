---
layout:     post
title:      LeetCode 162 Find Peak Element (Python)
number:     162
level:      Medium
lcurl:      find-peak-element
youtube:    
bilibili1:  
xigua:      
date:       2024-11-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

### 解题思路



### 代码
```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            if l == r:
                return l
            m = (l + r) // 2
            if nums[m - 1] < nums[m] > nums[m + 1]:
                return m
            if nums[m] < nums[m + 1]:
                l = m + 1
            else:
                r = m - 1
```
