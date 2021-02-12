---
layout:     post
title:      LeetCode 1342 Number of Steps to Reduce a Number to Zero (Python)
number:     1342
level:      Easy
lcurl:      number-of-steps-to-reduce-a-number-to-zero
youtube:    KwFYpgD-UAw
bilibili1:  //player.bilibili.com/player.html?aid=331671055&bvid=BV19A411T7qn&cid=296757549&page=1
xigua:      
date:       2021-02-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a non-negative integer num, return the number of steps to reduce it to zero. If the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

### 解题思路

按照题目要求模拟

### 代码
```python
class Solution:
    def numberOfSteps (self, num: int) -> int:
        res = 0
        while num:
            num = num - 1 if num & 1 else num >> 1
            res += 1
        return res
```
