---
layout:     post
title:      LeetCode 713 Subarray Product Less Than K (Python)
number:     713
level:      Medium
lcurl:      subarray-product-less-than-k
youtube:    k2rGcKXrkHk
bilibili1:  //player.bilibili.com/player.html?aid=457234559&bvid=BV1T5411j7tC&cid=239878040&page=1
xigua:      
date:       2020-09-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Your are given an array of positive integers nums.

Count and print the number of (contiguous) subarrays where the product of all the elements in the subarray is less than k.

### 解题思路

使用双指针，枚举右端点r，如果连续的乘积小于k，那么以r为右端点的成绩小于k的子数组的个数为r-l+1个，否则就向右移动左端点

### 代码
```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        if k <= 1:
            return 0
        prod = 1
        res = l = 0
        for r, val in enumerate(nums):
            prod *= val
            while prod >= k:
                prod /= nums[l]
                l += 1
            res += r - l + 1
        return res
```
