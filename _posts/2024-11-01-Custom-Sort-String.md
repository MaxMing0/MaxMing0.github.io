---
layout:     post
title:      LeetCode 791 Custom Sort String (Python)
number:     791
level:      Medium
lcurl:      custom-sort-string
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

You are given two strings order and s. All the characters of order are unique and were sorted in some custom order previously.

Permute the characters of s so that they match the order that order was sorted. More specifically, if a character x occurs before a character y in order, then x should occur before y in the permuted string.

Return any permutation of s that satisfies this property.

### 解题思路

方法一，用字典给每个字母一个数作为大小比较，没出现在order里的默认为-1，自定义排序比较函数

方法二，用counter求出每个字母出现的次数，遍历order，如果遇到出现的字母，就产生对此个数的字母，把所有没出现在order里的放到最后

### 代码
```python
class Solution:
    def customSortString(self, order: str, str: str) -> str:
        ct = Counter(str)
        res = []
        for c in order:
            res.append(c * ct[c])
            ct[c] = 0
        for c, v in ct.items():
            res.append(c * v)
        return ''.join(res)
```
```python
class Solution:
    def customSortString(self, order: str, str: str) -> str:
        d = {c: i for i, c in enumerate(order)}
        return ''.join(sorted(str, key=lambda x: d.get(x, -1)))
```
