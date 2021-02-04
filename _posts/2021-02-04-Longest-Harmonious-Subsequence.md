---
layout:     post
title:      LeetCode 594 Longest Harmonious Subsequence (Python)
number:     594
level:      Easy
lcurl:      longest-harmonious-subsequence
youtube:    _MYGyJ1PaUM
bilibili1:  //player.bilibili.com/player.html?aid=971518099&bvid=BV1Pp4y1p7ss&cid=292624815&page=1
xigua:      
date:       2021-02-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

We define a harmonious array as an array where the difference between its maximum value and its minimum value is exactly 1.

Given an integer array nums, return the length of its longest harmonious subsequence among all its possible subsequences.

A subsequence of array is a sequence that can be derived from the array by deleting some or no elements without changing the order of the remaining elements.

### 解题思路

统计每个数出现的次数，求连续两个数出现的最大次数

### 代码
```python
class Solution:
    def findLHS(self, nums: List[int]) -> int:
        c = Counter(nums)
        res = 0
        for x in c:
            if x + 1 in c:
                res = max(res, c[x] + c[x + 1])
        return res
```
