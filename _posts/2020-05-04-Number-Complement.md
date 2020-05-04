---
layout:     post
title:      LeetCode 476 Number Complement (Python)
number:     476
level:      Easy
lcurl:      number-complement
youtube:    ilFp-EMpdLw
bilibili1:  //player.bilibili.com/player.html?aid=838059168&bvid=BV1Lg4y167NB&cid=186896724&page=1
xigua:      
date:       2020-05-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

### 解题思路

对应一个n位数m，最后的结果为`(2**n - 1) ^ m` （2的n次幂减一的结果异或m）

### 代码
```python
class Solution:
    def findComplement(self, num: int) -> int:
        x = 1
        while x <= num:
            x <<= 1
        return (x - 1) ^ num
```
