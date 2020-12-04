---
layout:     post
title:      LeetCode 1492 The kth Factor of n (Python)
number:     1492
level:      Medium
lcurl:      the-kth-factor-of-n
youtube:    0gHkRXKC6e8
bilibili1:  //player.bilibili.com/player.html?aid=670606193&bvid=BV1ha4y1H7vz&cid=262761232&page=1
xigua:      
date:       2020-12-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given two positive integers n and k.

A factor of an integer n is defined as an integer i where n % i == 0.

Consider a list of all factors of n sorted in ascending order, return the kth factor in this list or return -1 if n has less than k factors.

### 解题思路

遍历1到根号n，找出n的因子，并同时存储相乘等于n的对应的因子，如果k比前面找到的因子多，再判断是否在后面存的因子中。要处理完全平方数的情况

### 代码
```python
class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        factor = []
        for i in range(1, int(math.sqrt(n)) + 1):
            if n % i == 0:
                k -= 1
                factor.append(n // i)
            if k == 0:
                return i
        if factor[-1] ** 2 == n:
            factor.pop()
        return -1 if k > len(factor) else factor[-k]
```
