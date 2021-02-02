---
layout:     post
title:      LeetCode 191 Number of 1 Bits (Python)
number:     191
level:      Easy
lcurl:      number-of-1-bits
youtube:    u-ehcQZLCD0
bilibili1:  //player.bilibili.com/player.html?aid=458931068&bvid=BV1i5411J7SA&cid=291325109&page=1
xigua:      
date:       2021-02-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

### 解题思路

每次&1判断是否最后一位为1，之后右移一位

### 代码
```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        res = 0
        while n:
            res += n & 1
            n >>= 1
        return res
```
