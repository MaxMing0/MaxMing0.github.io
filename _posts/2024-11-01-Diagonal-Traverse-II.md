---
layout:     post
title:      LeetCode 1424 Diagonal Traverse II (Python)
number:     1424
level:      Medium
lcurl:      diagonal-traverse-ii
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a 2D integer array nums, return all elements of nums in diagonal order as shown in the below images.

### 解题思路

i+j相同的格的数放在一行，从第一行开始遍历，由于从左下到右上，结果将每组翻转

### 代码
```python
class Solution:
    def findDiagonalOrder(self, nums: List[List[int]]) -> List[int]:
        maxij = 0
        tmp = defaultdict(list)
        for i in range(len(nums)):
            for j in range(len(nums[i])):
                tmp[i + j].append(nums[i][j])
                maxij = max(maxij, i + j)
        res = []
        for i in range(maxij + 1):
            res.extend(tmp[i][::-1])
        return res
```
