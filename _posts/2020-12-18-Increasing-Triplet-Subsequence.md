---
layout:     post
title:      LeetCode 334 Increasing Triplet Subsequence (Python)
number:     334
level:      Medium
lcurl:      increasing-triplet-subsequence
youtube:    xPKk7Zxyxe4
bilibili1:  //player.bilibili.com/player.html?aid=755698563&bvid=BV1Kr4y1F7m9&cid=268097316&page=1
xigua:      
date:       2020-12-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

### 解题思路

使用两个指针，一个记录最小的，一个记录次小的，如果再出现一个比两者都大的，则存在

### 代码
```python
class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        first = second = float('inf')
        for n in nums:
            if n <= first:
                first = n
            elif n <= second:
                second = n
            else:
                return True
        return False
```
