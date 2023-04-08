---
layout:     post
title:      LeetCode 2439 Minimize Maximum of Array (Python)
number:     2439
level:      Medium
lcurl:      minimize-maximum-of-array
youtube:    TY63fNliDL4
bilibili1:  
xigua:      
date:       2023-04-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given a 0-indexed array nums comprising of n non-negative integers.

In one operation, you must:

- Choose an integer i such that 1 <= i < n and nums[i] > 0.
- Decrease nums[i] by 1.
- Increase nums[i - 1] by 1.
Return the minimum possible value of the maximum integer of nums after performing any number of operations.

### 解题思路

因为每个数字只能往前移动，对于每个前缀数组的结果是，前缀和除以元素个数上取整

### 代码
```python
class Solution:
    def minimizeArrayValue(self, nums: List[int]) -> int:
        pre = res = nums[0]
        for i in range(1, len(nums)):
            pre += nums[i]
            res = max(res, math.ceil(pre / (i + 1)))
        return res
```
