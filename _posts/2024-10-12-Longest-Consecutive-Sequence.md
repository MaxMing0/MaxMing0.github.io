---
layout:     post
title:      LeetCode 128 Longest Consecutive Sequence (Python)
number:     128
level:      Medium
lcurl:      longest-consecutive-sequence
youtube:    
bilibili1:  
xigua:      
date:       2024-10-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Set
---

### 题目

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

### 解题思路



### 代码
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        s = set(nums)
        res = 0
        for n in nums:
            if n - 1 in s:
                continue
            cur = n + 1
            while cur in s:
                cur += 1
            res = max(res, cur - n)
        return res
```
