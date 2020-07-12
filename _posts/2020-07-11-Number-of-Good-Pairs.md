---
layout:     post
title:      LeetCode 1512 Number of Good Pairs (Python)
number:     1512
level:      Easy
lcurl:      number-of-good-pairs
youtube:    ArVYcxnhslw
bilibili1:  //player.bilibili.com/player.html?aid=456277582&bvid=BV1Q5411Y7oo&cid=211603303&page=1
xigua:      
date:       2020-07-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of integers nums.

A pair (i,j) is called good if nums[i] == nums[j] and i < j.

Return the number of good pairs.

### 解题思路

1. 枚举i j，进行比较
2. 计算每个数出现的次数n，那么可以构成`N * （n - 1）/ 2`组

### 代码
```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        n = len(nums)
        res = 0
        for i in range(n - 1):
            for j in range(i + 1, n):
                if nums[i] == nums[j]:
                    res += 1
        return res
```
```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        return sum(v * (v - 1) // 2 for v in Counter(nums).values())
```
