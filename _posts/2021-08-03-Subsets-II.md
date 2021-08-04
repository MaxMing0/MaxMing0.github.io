---
layout:     post
title:      LeetCode 90 Subsets II (Python)
number:     90
level:      Medium
lcurl:      subsets-ii
youtube:    e6muyxzoBmc
bilibili1:  //player.bilibili.com/player.html?aid=674586836&bvid=BV1EU4y1J7Wu&cid=382145243&page=1
xigua:      
date:       2021-08-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array nums that may contain duplicates, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

### 解题思路

先把所有数排序，从空集开始进行拓展，如果当前的数和上一个相同，只能拓展上一次的结果，否则可以拓展之前所有的结果

### 代码
```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        res = [[], [nums[0]]]
        tmp = [[nums[0]]]
        for i in range(1, len(nums)):
            if nums[i] == nums[i - 1]:
                tmp = [t + [nums[i]] for t in tmp]
            else:
                tmp = [t + [nums[i]] for t in res]
            res += tmp
        return res
```
