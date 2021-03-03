---
layout:     post
title:      LeetCode 268 Missing Number (Python)
number:     268
level:      Easy
lcurl:      missing-number
youtube:    6xKpoEiLTvE
bilibili1:  //player.bilibili.com/player.html?aid=671989422&bvid=BV1LU4y1p7n7&cid=305499497&page=1
xigua:      
date:       2021-03-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

Follow up: Could you implement a solution using only O(1) extra space complexity and O(n) runtime complexity?

### 解题思路

求出1-n的和，减去数组的总和

### 代码
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return (len(nums) + 1) * len(nums) // 2 - sum(nums)
```
