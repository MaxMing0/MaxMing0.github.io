---
layout:     post
title:      LeetCode 485 Max Consecutive Ones (Python)
number:     485
level:      Easy
lcurl:      max-consecutive-ones
youtube:    ClzerO5fSdk
bilibili1:  
xigua:      
date:       2022-02-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a binary array nums, return the maximum number of consecutive 1's in the array.

### 解题思路

遍历数组，遇到1计数器+1，遇到0更新结果同时计数器清零，单独处理最后一位不是0的情况

### 代码
```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        res = tmp = 0
        for n in nums:
            if n == 1:
                tmp += 1
            else:
                res = max(res, tmp)
                tmp = 0
        return max(res, tmp)
```
