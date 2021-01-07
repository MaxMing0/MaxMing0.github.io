---
layout:     post
title:      LeetCode 1539 Kth Missing Positive Number (Python)
number:     1539
level:      Easy
lcurl:      kth-missing-positive-number
youtube:    ngK2-0iLkq0
bilibili1:  //player.bilibili.com/player.html?aid=886065804&bvid=BV1QK4y1p7E3&cid=278443638&page=1
xigua:      
date:       2020-01-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.

Find the kth positive integer that is missing from this array.

### 解题思路

到第i个数ai，所缺失的正整数个数是ai-i-1，而且这个数是非严格递增的，所以可以用二分搜索要找的数所在的区间，答案为左边的位置+k

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
