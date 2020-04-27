---
layout:     post
title:      LeetCode 201 Bitwise AND of Numbers Range (Python)
number:     201
level:      Medium
lcurl:      bitwise-and-of-numbers-range
youtube:    CY1tnj53L_k
bilibili1:  //player.bilibili.com/player.html?aid=925458825&bvid=BV1dT4y1g75m&cid=182216832&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

### 解题思路



### 代码
```python
class Solution:
    def rangeBitwiseAnd(self, m: int, n: int) -> int:
        if len(bin(m)) != len(bin(n)):
            return 0
        res = 0
        while (m != n):
            m >>= 1
            n >>= 1
            res += 1
        return m << res
```