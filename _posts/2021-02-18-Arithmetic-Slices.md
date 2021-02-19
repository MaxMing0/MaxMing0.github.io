---
layout:     post
title:      LeetCode 413 Arithmetic Slices  (Python)
number:     413
level:      Medium
lcurl:      arithmetic-slices
youtube:    R-9AxyTXbpI
bilibili1:  //player.bilibili.com/player.html?aid=289369303&bvid=BV13f4y167YZ&cid=299680476&page=1
xigua:      
date:       2021-02-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

A sequence of numbers is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, these are arithmetic sequences:

1, 3, 5, 7, 9
7, 7, 7, 7
3, -1, -5, -9
The following sequence is not arithmetic.

1, 1, 2, 5, 7
 
A zero-indexed array A consisting of N numbers is given. A slice of that array is any pair of integers (P, Q) such that 0 <= P < Q < N.

A slice (P, Q) of the array A is called arithmetic if the sequence:
A[P], A[P + 1], ..., A[Q - 1], A[Q] is arithmetic. In particular, this means that P + 1 < Q.

The function should return the number of arithmetic slices in the array A.

### 解题思路

如果连续n个数是等差，低n个数可以增加n-2个序列，遍历数组，记录之前的序列个数，加到结果里

### 代码
```python
class Solution:
    def numberOfArithmeticSlices(self, A: List[int]) -> int:
        res = 0
        t = 1
        for i in range(2, len(A)):
            if A[i] - A[i - 1] == A[i - 1] - A[i - 2]:
                res += t
                t += 1
            else:
                t = 1
        return res
```
