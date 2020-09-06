---
layout:     post
title:      LeetCode 835 Image Overlap (Python)
number:     835
level:      Medium
lcurl:      image-overlap
youtube:    s7V7GPv1Mzs
bilibili1:  //player.bilibili.com/player.html?aid=884525342&bvid=BV1NK4y1a7Yf&cid=232787012&page=1
xigua:      
date:       2020-09-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Two images A and B are given, represented as binary, square matrices of the same size.  (A binary matrix has only 0s and 1s as values.)

We translate one image however we choose (sliding it left, right, up, or down any number of units), and place it on top of the other image.  After, the overlap of this translation is the number of positions that have a 1 in both images.

(Note also that a translation does not include any kind of rotation.)

What is the largest possible overlap?

### 解题思路

枚举两个矩阵，如果都是1，则计算让这两个1重叠的移动方向，最后统计哪个移动方向重叠的1最多

### 代码
```python
class Solution:
    def largestOverlap(self, A: List[List[int]], B: List[List[int]]) -> int:
        N = len(A)
        ct = collections.Counter()
        for i, row in enumerate(A):
            for j, col in enumerate(row):
                if col:
                    for i2, row2 in enumerate(B):
                        for j2, col2 in enumerate(row2):
                            if col2:
                                ct[i - i2, j - j2] += 1
        return max(ct.values() or [0])
```
