---
layout:     post
title:      LeetCode 1442 Count Triplets That Can Form Two Arrays of Equal XOR (Python)
number:     1442
level:      Medium
lcurl:      https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/
youtube:    u70mlKtZMLU
bilibili1:  
xigua:      
date:       2020-05-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
    - Math
---

### 题目

Given an array of integers arr.

We want to select three indices i, j and k where (0 <= i < j <= k < arr.length).

Let's define a and b as follows:

`a = arr[i] ^ arr[i + 1] ^ ... ^ arr[j - 1]`

`b = arr[j] ^ arr[j + 1] ^ ... ^ arr[k]`

Note that ^ denotes the bitwise-xor operation.

Return the number of triplets (i, j and k) Where a == b.

### 解题思路

由下面的式子我们可以使用类似部分和的思想，快速求出连续数组的异或的结果
```
X = a0 ^ a1 ^ ... ^ ai-1
Y = a0 ^ a1 ^ ... ^ ai-1 ^ ai ^ ...^ aj-1
Z = a0 ^ a1 ^ ... ^ ai-1 ^ ai ^ ...^ aj-1 ^ aj ^ ... ^ ak
X ^ Y = ai ^ ...^ aj-1
Y ^ Z = aj ^ ... ^ ak
```
就先求出这个数组，然后遍历ijk，只需要判断`X^Y`与`Y^Z`是否相等，来决定是不是一组解

### 代码
```python
class Solution:
    def countTriplets(self, arr: List[int]) -> int:
        n = len(arr)
        ps = [0] * (n + 1)
        for i in range(n):
            ps[i + 1] = ps[i] ^ arr[i]
        res = 0
        for i in range(n - 1):
            for j in range(i + 1, n):
                for k in range(j, n):
                    if ps[i] ^ ps[j] == ps[j] ^ ps[k + 1]:
                        res += 1
        return res
```
