---
layout:     post
title:      LeetCode 1748 Sum of Unique Elements (Python)
number:     1748
level:      Easy
lcurl:      sum-of-unique-elements
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashMap
---

### 题目

You are given an integer array nums. The unique elements of an array are the elements that appear exactly once in the array.

Return the sum of all the unique elements of nums.

### 解题思路

使用Counter求出每个数出现的次数

### 代码
```python
class Solution:
    def sumOfUnique(self, nums: List[int]) -> int:
        ct = Counter(nums)
        res = 0
        for key, val in ct.items():
            if val == 1:
                res += key
        return res
```
