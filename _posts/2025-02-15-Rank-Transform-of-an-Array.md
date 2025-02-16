---
layout:     post
title:      LeetCode 1331 Rank Transform of an Array (Python)
number:     1331
level:      Easy
lcurl:      rank-transform-of-an-array
youtube:    
bilibili1:  
xigua:      
date:       2025-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given an array of integers arr, replace each element with its rank.

The rank represents how large the element is. The rank has the following rules:

- Rank is an integer starting from 1.
- T he larger the element, the larger the rank. If two elements are equal, their rank must be the same.
- Rank should be as small as possible.

### 解题思路

给所有的数去重再排序，用字典记录rank，在遍历数组，用rank替换。

### 代码
```python
class Solution:
    def arrayRankTransform(self, arr: List[int]) -> List[int]:
        dic = {}
        rank = 1
        for n in sorted(set(arr)):
            dic[n] = rank
            rank += 1
        for i in range(len(arr)):
            arr[i] = dic[arr[i]]
        return arr
```
