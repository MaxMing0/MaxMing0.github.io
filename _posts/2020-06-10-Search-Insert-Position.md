---
layout:     post
title:      LeetCode 35 Search Insert Position (Introduce python bisect) (Python)
number:     35
level:      Easy
lcurl:      search-insert-position
youtube:    vjDKqFHVXOM
bilibili1:  //player.bilibili.com/player.html?aid=285985012&bvid=BV1wf4y1m7Ue&cid=200604236&page=1
xigua:      
date:       2020-06-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

### 解题思路

二分搜索

### 代码
```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        # return bisect.bisect_left(nums, target)
        
        l, r = 0, len(nums) - 1
        while l <= r:
            m = (l + r) // 2
            if nums[m] == target:
                return m
            if nums[m] < target:
                l = m + 1
            else:
                r = m - 1
        return l
```
