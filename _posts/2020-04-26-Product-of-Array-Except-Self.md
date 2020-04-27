---
layout:     post
title:      LeetCode 238 Product of Array Except Self (Python)
number:     238
level:      Medium
lcurl:      product-of-array-except-self
youtube:    cABFWnZfO0g
bilibili1:  //player.bilibili.com/player.html?aid=925335237&bvid=BV1oT4y1G78Y&cid=178680117&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an array nums of n integers where n > 1,  return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

### 解题思路



### 代码
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        l = len(nums)
        res = [1] * l
        # l -> r
        for i in range(1, l):
            res[i] = res[i - 1] * nums[i - 1]
        # r -> l
        productR = 1
        for i in range(l-1, -1, -1):
            res[i] *= productR
            productR *= nums[i]
        return res
```