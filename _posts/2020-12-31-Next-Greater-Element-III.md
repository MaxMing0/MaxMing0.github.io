---
layout:     post
title:      LeetCode 556 Next Greater Element III (Python)
number:     556
level:      Medium
lcurl:      next-greater-element-iii
youtube:    GcKJJutl7WI
bilibili1:  
xigua:      
date:       2020-12-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a positive integer n, find the smallest integer which has exactly the same digits existing in the integer n and is greater in value than n. If no such positive integer exists, return -1.

Note that the returned integer should fit in 32-bit integer, if there is a valid answer but it does not fit in 32-bit integer, return -1.

### 解题思路

从后向前找到第一个升序的位置（如果不存在，返回-1），将这个数与从后向前第一个比它大的数进行交换，再把后面的数从小到大排序

### 代码
```python
class Solution:
    def nextGreaterElement(self, n: int) -> int:
        s = list(str(n))
        l = len(s)
        i = l - 2
        while i >= 0:
            if s[i] < s[i + 1]:
                break
            i -= 1
        if i < 0:
            return -1
        for j in range(l - 1, i, -1):
            if s[j] > s[i]:
                s[i], s[j] = s[j], s[i]
                break
        s[i + 1:] = s[i + 1:][::-1]
        res = ''.join(s)
        return res if int(res) <= 0x7fffffff else -1
```
