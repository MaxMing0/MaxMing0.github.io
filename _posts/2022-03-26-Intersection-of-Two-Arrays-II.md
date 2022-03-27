---
layout:     post
title:      LeetCode 350 Intersection of Two Arrays II (Python)
number:     350
level:      Easy
lcurl:      intersection-of-two-arrays-ii
youtube:    LY_rNpRpSfE
bilibili1:  
xigua:      
date:       2022-03-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

### 解题思路

将一个数组转换成计数器，遍历第二个数组，如果在第一个数组中出现，并且出现的个数大于0，则加到结果里，出现次数减一

### 代码
```python
from collections import Counter
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        ct = Counter(nums1)
        res = []
        for n in nums2:
            if ct[n]:
                res.append(n)
                ct[n] -= 1
        return res
```
