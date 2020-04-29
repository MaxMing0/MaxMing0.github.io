---
layout:     post
title:      LeetCode 33 Search in Rotated Sorted Array (Python)
number:     33
level:      Medium
lcurl:      search-in-rotated-sorted-array
youtube:    vFCl7cb0VSk
bilibili1:  //player.bilibili.com/player.html?aid=625292617&bvid=BV14t4y127hK&cid=180487284&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

### 解题思路

和没有被rotate过的一样，使用二分的方法，我们总和考虑二分时候的左(L)右(R)端点，中点(M)和目标(T)

L <= M < T, T < L <= M, M < T < L，当这三种情况出现时，移动L到M+1，其他情况移动R到M-1

### 代码
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            m = (l + r) // 2
            if nums[m] == target:
                return m
            elif nums[l] <= nums[m] < target or \
                target < nums[l] <= nums[m] or \
                nums[m] < target < nums[l]:
                l = m + 1
            else:
                r = m - 1
        return -1
```
