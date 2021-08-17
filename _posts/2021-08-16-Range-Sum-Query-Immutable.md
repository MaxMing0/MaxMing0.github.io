---
layout:     post
title:      LeetCode 303 Range Sum Query - Immutable (Python)
number:     303
level:      Easy
lcurl:      range-sum-query-immutable
youtube:    -bUAs9opC3o
bilibili1:  //player.bilibili.com/player.html?aid=377380683&bvid=BV1Ho4y1U7wF&cid=390837141&page=1
xigua:      
date:       2021-06-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Prefix Sum
---

### 题目

Given an integer array nums, handle multiple queries of the following type:

1. Calculate the sum of the elements of nums between indices left and right inclusive where left <= right.
Implement the NumArray class:

- NumArray(int[] nums) Initializes the object with the integer array nums.
- int sumRange(int left, int right) Returns the sum of the elements of nums between indices left and right inclusive (i.e. nums[left] + nums[left + 1] + ... + nums[right]).


### 解题思路

前缀和

### 代码
```python
class NumArray:

    def __init__(self, nums: List[int]):
        self.prefix_sum = [0]
        for n in nums:
            self.prefix_sum.append(self.prefix_sum[-1] + n)

    def sumRange(self, left: int, right: int) -> int:
        return self.prefix_sum[right + 1] - self.prefix_sum[left]
```
