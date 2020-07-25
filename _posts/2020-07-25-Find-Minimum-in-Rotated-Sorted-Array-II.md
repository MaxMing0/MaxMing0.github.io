---
layout:     post
title:      LeetCode 154 Find Minimum in Rotated Sorted Array II (Python)
number:     154
level:      Hard
lcurl:      find-minimum-in-rotated-sorted-array-ii
youtube:    XmAjWFn28VQ
bilibili1:  //player.bilibili.com/player.html?aid=753915866&bvid=BV1ik4y1B7de&cid=216447439&page=1
xigua:      
date:       2020-07-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).

Find the minimum element.

The array may contain duplicates.

### 解题思路

如果二分中点小于右边，右端点移动到中点，大于右边，左端点移动到中点+1，相等，右端点减一

### 代码
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1
        while l < r:
            m = (l + r) // 2
            if nums[m] < nums[r]:
                r = m
            elif nums[m] > nums[r]:
                l = m + 1
            else:
                r -= 1
        return nums[l]
```
