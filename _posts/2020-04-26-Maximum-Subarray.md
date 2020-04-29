---
layout:     post
title:      LeetCode 53 Maximum Subarray (Python)
number:     53
level:      Easy
lcurl:      happy-number
youtube:    9RCR1vyJq5A
bilibili1:  //player.bilibili.com/player.html?aid=327546128&bvid=BV11A41187AR&cid=173439380&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
    - Math
---

### 题目
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

### 解题思路

贪心，到当前位置并且包括当前数字的最大子数组，可以是这个数自己，或者自己加上之前上到上一个数的最大子数组

cur = max(nums[i], cur + nums[i])

### 代码
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        res = cur = nums[0]
        for n in nums[1:]:
            cur = max(cur + n, n)
            res = max(res, cur)
        return res
```
