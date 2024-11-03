---
layout:     post
title:      LeetCode 163 Missing Ranges (Python)
number:     163
level:      Easy
lcurl:      missing-ranges
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

You are given an inclusive range [lower, upper] and a sorted unique integer array nums, where all elements are within the inclusive range.

A number x is considered missing if x is in the range [lower, upper] and x is not in nums.

Return the shortest sorted list of ranges that exactly covers all the missing numbers. That is, no element of nums is included in any of the ranges, and each missing number is covered by one of the ranges.

### 解题思路

维护一个need=lower，为下次希望遇到的数，如果等于need，则need+1，大于need，则增加从need到n-1的区间，need+1，如果最后need<=upper,加入need到upper的区间

### 代码
```python
class Solution:
    def findMissingRanges(self, nums: List[int], lower: int, upper: int) -> List[List[int]]:
        need, res = lower, []
        for n in nums:
            if n == need:
                need += 1
            else:
                res.append([need, n - 1])
                need = n + 1
        if need <= upper:
            res.append([need, upper])
        return res
```
