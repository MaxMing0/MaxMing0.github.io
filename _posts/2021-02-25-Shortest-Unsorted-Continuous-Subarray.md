---
layout:     post
title:      LeetCode 581 Shortest Unsorted Continuous Subarray (Python)
number:     581
level:      Medium
lcurl:      shortest-unsorted-continuous-subarray
youtube:    IUT5Mo1wBaw
bilibili1:  //player.bilibili.com/player.html?aid=844371910&bvid=BV1Y54y1h7Xa&cid=302669865&page=1
xigua:      
date:       2021-02-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer array nums, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order.

Return the shortest such subarray and output its length.

### 解题思路

用排好序的数组与原数组进行比较，找到第一个与最后一个不相同的位置，这两个位置直接需要排序

### 代码
```python
class Solution:
    def findUnsortedSubarray(self, nums: List[int]) -> int:
        order = [x == y for x, y in zip(nums, sorted(nums))]
        return 0 if all(order) else (len(nums)) - order.index(False) - order[::-1].index(False)
```
