---
layout:     post
title:      LeetCode 215 Kth Largest Element in an Array (Python)
number:     215
level:      Medium
lcurl:      kth-largest-element-in-an-array
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Heap
---

### 题目

Given an integer array nums and an integer k, return the kth largest element in the array.

Note that it is the kth largest element in the sorted order, not the kth distinct element.

Can you solve it without sorting?

### 解题思路

方法一，维护一个大小为k的heap，把所有数字依次加入进去，堆中的最小值为最后的结果

方法二，使用quickselect

### 代码
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        q = []
        for n in nums:
            if len(q) == k:
                heapq.heappushpop(q, n)
            else:
                heapq.heappush(q, n)
        return min(q)
```
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        def quickSelect(nums, l, r, k):
            i, j, pivot = l, r, nums[r]
            while i < j:
                if nums[i] > pivot:
                    j -= 1
                    nums[i], nums[j] = nums[j], nums[i]
                else:
                    i += 1
            nums[i], nums[r] = nums[r], nums[i]
            m = i - l + 1
            if m == k:
                return i
            elif m > k:
                return quickSelect(nums, l, i - 1, k)
            else:
                return quickSelect(nums, i + 1, r, k - m)

        n = len(nums)
        return nums[quickSelect(nums, 0, n - 1, n - k + 1)]
```
