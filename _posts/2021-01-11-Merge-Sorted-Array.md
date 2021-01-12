---
layout:     post
title:      LeetCode 88 Merge Sorted Array (Python)
number:     88
level:      Easy
lcurl:      merge-sorted-array
youtube:    7tPnvDf1cvM
bilibili1:  //player.bilibili.com/player.html?aid=843649791&bvid=BV1g54y1s7ZG&cid=281387947&page=1
xigua:      
date:       2020-01-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

The number of elements initialized in nums1 and nums2 are m and n respectively. You may assume that nums1 has enough space (size that is equal to m + n) to hold additional elements from nums2.

### 解题思路

使用三个指针，两个指向两个数组有数部分的结尾，第三个指向第一个数组末尾，依次比较两个数组较小的数，放到第三个指针的位置

### 代码
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i, j, k = m - 1, n - 1, m + n - 1
        while i >= 0 and j >= 0:
            if nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i, k = i - 1, k - 1
            else:
                nums1[k] = nums2[j]
                j, k = j - 1, k - 1
        while j >= 0:
            nums1[k] = nums2[j]
            j, k = j - 1, k - 1
```
