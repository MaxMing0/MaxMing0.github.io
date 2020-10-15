---
layout:     post
title:      LeetCode 189 Rotate Array (Python)
number:     189
level:      Medium
lcurl:      rotate-array
youtube:    eqwsx2UmhQk
bilibili1:  //player.bilibili.com/player.html?aid=457390620&bvid=BV1N541177Bk&cid=245905772&page=1
xigua:      
date:       2020-10-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an array, rotate the array to the right by k steps, where k is non-negative.

Follow up:
- Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?

### 解题思路

对数组进行翻转，之后对前k个和后n-k个数分别进行翻转

### 代码
```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def rev(nums, l, r):
            while l < r:
                nums[l], nums[r] = nums[r], nums[l]
                l += 1
                r -= 1
        
        n = len(nums)
        k %= n
        rev(nums, 0, n - 1)
        rev(nums, 0, k - 1)
        rev(nums, k, n - 1)
```
