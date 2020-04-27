---
layout:     post
title:      LeetCode 283 Move Zeroes (Python)
number:     283
level:      Easy
lcurl:      move-zeroes
youtube:    QVazS8Mor_4
bilibili1:  //player.bilibili.com/player.html?aid=667614499&bvid=BV1ba4y1t7eK&cid=173834262&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

### 解题思路



### 代码
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l, r, n = 0, 0, len(nums)
        while r < n:
            if nums[r] != 0:
                nums[l] = nums[r]
                l += 1
            r += 1
        while l < n:
            nums[l] = 0
            l += 1
```