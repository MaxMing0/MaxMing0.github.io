---
layout:     post
title:      LeetCode 16 3Sum Closest (Python)
number:     16
level:      Medium
lcurl:      3sum-closest
youtube:    
bilibili1:  
xigua:      
date:       2024-11-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.

### 解题思路

把数组排序，枚举第一个数，之后两个指针枚举后两个数，维护一个与target的差值的最小gap

### 代码
```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        gap = float("inf")
        for i in range(len(nums)):
            cur = nums[i]
            j = i + 1
            k = len(nums) -1
            while j < k:
                tmp = nums[i] + nums[j] + nums[k] - target
                gap = tmp if abs(tmp) < abs(gap) else gap
                if tmp > 0:
                    k -= 1
                elif tmp < 0:
                    j += 1
                else:
                    return target
        return target + gap
```
