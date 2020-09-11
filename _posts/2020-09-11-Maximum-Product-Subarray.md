---
layout:     post
title:      LeetCode 152 Maximum Product Subarray (Python)
number:     152
level:      Medium
lcurl:      maximum-product-subarray
youtube:    G_Hs4qMuiAI
bilibili1:  //player.bilibili.com/player.html?aid=499554013&bvid=BV1iK411K7yG&cid=234300867&page=1
xigua:      
date:       2020-09-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array nums, find the contiguous subarray within an array (containing at least one number) which has the largest product.

### 解题思路

如果数组包含0，则先分成若干个不含0的部分，分别求结果
- 如果有1个负数，结果为两端不包含这个数较大乘积
- 如果有偶数个负数，结果为所有数乘积
- 如果有奇数个负数，则为第一个负数后面所有数乘积，或者最后一个负数，前面所有数的成绩
- 第1和第3种情况可以合并

### 代码
```python
class Solution:
    def solve(self, nums):
        def mul(n):
            return reduce(lambda x, y: x * y, n, 1)
        if len(nums) == 0:
            return 0
        if len(nums) == 1:
            return nums[0]
        firstneg, lastneg, numneg = -1, -1, 0
        for i, n in enumerate(nums):
            if n < 0 :
                if firstneg == -1:
                    firstneg = i
                lastneg = i
                numneg += 1
        if numneg % 2 == 0:
            return mul(nums)
        return max(mul(nums[firstneg + 1:]), mul(nums[:lastneg]))
    
    def maxProduct(self, nums: List[int]) -> int:
        res = float('-inf')
        pre = 0
        for i, n in enumerate(nums):
            if n == 0:
                res = max(res, self.solve(nums[pre: i]))
                pre = i + 1
        res = max(res, self.solve(nums[pre:]))
        return res if pre == 0 else max(res, 0)
```
