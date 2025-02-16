---
layout:     post
title:      LeetCode 1539 Kth Missing Positive Number (Python)
number:     1539
level:      Easy
lcurl:      kth-missing-positive-number
youtube:    
bilibili1:  
xigua:      
date:       2025-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.

Return the kth positive integer that is missing from this array.

### 解题思路

二分，`arr[mid] - mid - 1`为缺少的数字个数

### 代码
```python
class Solution:
    def findKthPositive(self, arr: List[int], k: int) -> int:
        left, right = 0, len(arr) - 1
        while left <= right:
            mid = (left + right) // 2
            if arr[mid] - mid - 1 < k:
                left = mid + 1
            else:
                right = mid - 1
        return left + k
```
