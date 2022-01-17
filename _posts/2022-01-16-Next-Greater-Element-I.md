---
layout:     post
title:      LeetCode 496 Next Greater Element I (Python)
number:     496
level:      Easy
lcurl:      next-greater-element-i
youtube:    klQvIM6HVcg
bilibili1:  
xigua:      
date:       2022-01-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.

You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.

For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.

Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.

### 解题思路

使用单调栈处理nums2，找到每个元素后面最大的数是什么，将结果存在字典中，再通过nums1，生成结果

### 代码
```python
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        res = {}
        s = []
        for n in nums2[::-1]:
            while s and n >= s[-1]:
                s.pop()
            res[n] = s[-1] if s else -1
            s.append(n)
        return [res[n] for n in nums1]
```
