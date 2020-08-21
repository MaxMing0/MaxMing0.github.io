---
layout:     post
title:      LeetCode 905 Sort Array By Parity (Python)
number:     905
level:      Easy
lcurl:      sort-array-by-parity
youtube:    xFWrMgPJTV4
bilibili1:  //player.bilibili.com/player.html?aid=754257353&bvid=BV1Xk4y117rK&cid=227083335&page=1
xigua:      
date:       2020-08-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.

You may return any answer array that satisfies this condition.

### 解题思路

前后两个指针，如果前面的指向的是奇数，则从后面找到一个偶数进行交换

### 代码
```python
class Solution:
    def sortArrayByParity(self, A: List[int]) -> List[int]:
        l, r = 0, len(A) - 1
        while l < r:
            if A[l] % 2:
                while l < r and A[r] % 2:
                    r -= 1
                A[l], A[r] = A[r], A[l]
            l += 1
        return A
```
