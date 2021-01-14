---
layout:     post
title:      LeetCode 1658 Minimum Operations to Reduce X to Zero (Python)
number:     1658
level:      Medium
lcurl:      minimum-operations-to-reduce-x-to-zero
youtube:    wXtfMuRYfxI
bilibili1:  //player.bilibili.com/player.html?aid=628656929&bvid=BV18t4y1z7Hq&cid=282525873&page=1
xigua:      
date:       2020-01-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sliding Window
---

### 题目

You are given an integer array nums and an integer x. In one operation, you can either remove the leftmost or the rightmost element from the array nums and subtract its value from x. Note that this modifies the array for future operations.

Return the minimum number of operations to reduce x to exactly 0 if it's possible, otherwise, return -1.

### 解题思路

题目相当于求一个最长的连续子数组，和为sum-x，使用两个指针，通过滑动窗口找到最长的子数组

### 代码
```python
class Solution:
    def minOperations(self, nums: List[int], x: int) -> int:
        target = sum(nums) - x
        if target == 0:
            return len(nums)
        if target < 0:
            return -1
        l, r, window = 0, 0, 0
        max_len = -1
        while r < len(nums):
            window += nums[r]
            r += 1
            while window >= target:
                if (window == target):
                    max_len = max(max_len, r - l)
                window -= nums[l]
                l += 1
        return -1 if max_len == -1 else len(nums) - max_len
```
