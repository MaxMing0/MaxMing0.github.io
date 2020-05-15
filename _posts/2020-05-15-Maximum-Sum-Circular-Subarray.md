---
layout:     post
title:      LeetCode 918 Maximum Sum Circular Subarray (Python)
number:     918
level:      Medium
lcurl:      maximum-sum-circular-subarray
youtube:    KWyWBouPvCQ
bilibili1:  player.bilibili.com/player.html?aid=455628871&bvid=BV1c5411s7jZ&cid=191278187&page=1
xigua:      
date:       2020-05-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given a circular array C of integers represented by A, find the maximum possible sum of a non-empty subarray of C.

Here, a circular array means the end of the array connects to the beginning of the array.  (Formally, C[i] = A[i] when 0 <= i < A.length, and C[i+A.length] = C[i] when i >= 0.)

Also, a subarray may only include each element of the fixed buffer A at most once.  (Formally, for a subarray C[i], C[i+1], ..., C[j], there does not exist i <= k1, k2 <= j with k1 % A.length = k2 % A.length.)

### 解题思路

使用[第53题Maximum Subarray](https://maxming0.github.io/2020/04/26/Maximum-Subarray/)的方法，求出数组中连续最大和最小的子数组

最后的结果可以是最大的子数组或者所有数的和减去最小的子数组的和，要单独处理全是负数的情况

### 代码
```python
class Solution:
    def maxSubarraySumCircular(self, A: List[int]) -> int:
        max_cur = max_glo = min_cur = min_glo = A[0]
        for n in A[1:]:
            max_cur = max(n, n + max_cur)
            max_glo = max(max_glo, max_cur)
            min_cur = min(n, n + min_cur)
            min_glo = min(min_glo, min_cur)
        s = sum(A)
        if s == min_glo:
            return max_glo
        return max(max_glo, s - min_glo)
```
