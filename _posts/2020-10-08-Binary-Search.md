---
layout:     post
title:      LeetCode 704 Binary Search (Python)
number:     704
level:      Easy
lcurl:      binary-search
youtube:    5CXwAQBGNUg
bilibili1:  //player.bilibili.com/player.html?aid=669790053&bvid=BV1qa4y157E4&cid=243525772&page=1
xigua:      
date:       2020-10-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given a sorted (in ascending order) integer array nums of n elements and a target value, write a function to search target in nums. If target exists, then return its index, otherwise return -1.

### 解题思路

通过左右边界找到中点，如果为要找的数返回下标，否则移动边界，找不到，返回-1

### 代码
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            m = (l + r) // 2
            if nums[m] == target:
                return m
            if nums[m] < target:
                l = m + 1
            else:
                r = m - 1
        return -1
```
