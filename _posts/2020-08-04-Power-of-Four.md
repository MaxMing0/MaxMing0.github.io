---
layout:     post
title:      LeetCode 342 Power of Four (Python)
number:     342
level:      Easy
lcurl:      power-of-four
youtube:    bggMkroxefU
bilibili1:  //player.bilibili.com/player.html?aid=456543763&bvid=BV1p5411a7h1&cid=220319030&page=1
xigua:      
date:       2020-08-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

### 解题思路

一个数是4的幂一定是2的幂，区别是对3取余的结果不同

### 代码
```python
class Solution:
    def isPowerOfFour(self, num: int) -> bool:
        return num > 0 and num & (num - 1) == 0 and num % 3 == 1
```
