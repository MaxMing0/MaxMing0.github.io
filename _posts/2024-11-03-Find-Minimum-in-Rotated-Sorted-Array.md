---
layout:     post
title:      LeetCode 153 Find Minimum in Rotated Sorted Array (Python)
number:     153
level:      Medium
lcurl:      find-minimum-in-rotated-sorted-array
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

- [4,5,6,7,0,1,2] if it was rotated 4 times.
- [0,1,2,4,5,6,7] if it was rotated 7 times.
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of unique elements, return the minimum element of this array.

You must write an algorithm that runs in O(log n) time.

### 解题思路

首先判断，如果没有旋转，返回第一个数

进行二分，如果中间数大于下一个数，或者中间数小于前一个数，返回结果。如果中间数大于第一个数，在右边二分，否则在左边二分

### 代码
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        n = len(nums)
        if n == 1:
            return nums[0]
        if nums[-1] > nums[0]:
            return nums[0]
        l, r = 0, n - 1
        while l <= r:
            m = (l + r) // 2
            if nums[m] > nums[m + 1]:
                return nums[m + 1]
            if nums[m] < nums[m - 1]:
                return nums[m]
            if nums[m] > nums[0]:
                l = m + 1
            else:
                r = m - 1
```
