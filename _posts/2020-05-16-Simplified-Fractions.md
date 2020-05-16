---
layout:     post
title:      LeetCode Leetcode 1447 Simplified Fractions (Python)
number:     1447
level:      Medium
lcurl:      simplified-fractions
youtube:    M2RdBz-k0Dw
bilibili1:  player.bilibili.com/player.html?aid=328159525&bvid=BV1aA411t7Ez&cid=191912773&page=1
xigua:      
date:       2020-05-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given an integer n, return a list of all simplified fractions between 0 and 1 (exclusive) such that the denominator is less-than-or-equal-to n. The fractions can be in any order.

### 解题思路

遍历所有分子分母的可能，如果分子分母的最大公约数是1，则是一个要返回的结果

### 代码
```python
class Solution:
    def simplifiedFractions(self, n: int) -> List[str]:
        def gcd(x, y):
            return y if x == 0 else gcd(y % x, x)
        
        return ["%s/%s" % (i, j) for j in range(2, n + 1) for i in range(1, j) if gcd(i, j) == 1]
```
