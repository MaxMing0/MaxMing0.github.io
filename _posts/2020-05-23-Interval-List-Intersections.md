---
layout:     post
title:      LeetCode 986 Interval List Intersections (Python)
number:     986
level:      Medium
lcurl:      interval-list-intersections
youtube:    KfseZ3kdDiE
bilibili1:  //player.bilibili.com/player.html?aid=838312247&bvid=BV1wg4y1z7Xz&cid=194274868&page=1
xigua:      
date:       2020-05-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

Given two lists of closed intervals, each list of intervals is pairwise disjoint and in sorted order.

Return the intersection of these two interval lists.

### 解题思路

两个指针分别指向两个数组的区间，如果两个区间不想交，移动结束位置靠前的区间到下一个位置。

如果两个区间相交，求出相交的区间，同样移动结束位置靠前的区间到下一个位置。

### 代码
```python
class Solution:
    def intervalIntersection(self, A: List[List[int]], B: List[List[int]]) -> List[List[int]]:
        i, j, res = 0, 0, []
        while i < len(A) and j < len(B):
            if A[i][1] < B[j][0]:
                i += 1
            elif B[j][1] < A[i][0]:
                j += 1
            else:
                res.append([max(A[i][0], B[j][0]), min(A[i][1], B[j][1])]) 
                if A[i][1] < B[j][1]:
                    i += 1
                else:
                    j += 1
        return res
```
