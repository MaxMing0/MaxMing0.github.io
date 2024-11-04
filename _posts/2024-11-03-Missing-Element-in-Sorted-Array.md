---
layout:     post
title:      LeetCode 1060 Missing Element in Sorted Array (Python)
number:     1060
level:      Medium
lcurl:      missing-element-in-sorted-array
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given an integer array nums which is sorted in ascending order and all of its elements are unique and given also an integer k, return the kth missing number starting from the leftmost number of the array.

### 解题思路



### 代码
```python
class Solution:
    def missingElement(self, nums: List[int], k: int) -> int:
        n = len(nums)
        l, r = 0, n - 1
        while l <= r:
            mid = (l + r) // 2
            if (nums[mid] - nums[0]) - mid < k:
                l = mid + 1
            else:
                r = mid - 1
        return nums[0] + k + l - 1

class Solution:
    def missingElement(self, nums: List[int], k: int) -> int:
        for i in range(len(nums) - 1):
            miss = nums[i + 1] - nums[i] - 1
            if miss < k:
                k -= miss
            else:
                return nums[i] + k
        return nums[-1] + k
```
