---
layout:     post
title:      LeetCode 119 Pascal's Triangle II (Python)
number:     119
level:      Easy
lcurl:      pascals-triangle-ii
youtube:    aMljshiDTPE
bilibili1:  //player.bilibili.com/player.html?aid=541711239&bvid=BV1Ni4y1g7Lv&cid=223525402&page=1
xigua:      
date:       2020-08-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle.

Note that the row index starts from 0.

### 解题思路

对于每一行，从后向前求，就不需要额外空间了

### 代码
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        res = [1]
        for i in range(rowIndex):
            for j in range(i, 0, -1):
                res[j] += res[j - 1]
            res.append(1)
        return res
```
