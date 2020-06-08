---
layout:     post
title:      LeetCode 231 Power of Two (Python)
number:     231
level:      Easy
lcurl:      power-of-two
youtube:    pfRde1wSqSs
bilibili1:  //player.bilibili.com/player.html?aid=413486006&bvid=BV1rV411r7AL&cid=199957411&page=1
xigua:      
date:       2020-06-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given an integer, write a function to determine if it is a power of two.

### 解题思路

如果一个数`n`不为0，那么这个数是2的幂与`n & (n - 1) = 0`为充要条件

### 代码
```python
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n and not (n & (n - 1))
```
