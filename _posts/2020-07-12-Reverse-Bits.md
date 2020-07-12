---
layout:     post
title:      LeetCode 190 Reverse Bits (Python)
number:     190
level:      Easy
lcurl:      reverse-bits
youtube:    JtQki_voIWA
bilibili1:  //player.bilibili.com/player.html?aid=243821107&bvid=BV1qv411i7Wg&cid=211848241&page=1
xigua:      
date:       2020-07-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Reverse bits of a given 32 bits unsigned integer.

### 解题思路

1. 每次取这个数的最后一位，然后将其左移到对应的位置，加到结果里
2. 转换成二进制字符串，然后翻转

### 代码
```python
class Solution:
    def reverseBits(self, n: int) -> int:
        res, power = 0, 31
        while n:
            res += (n & 1) << power
            n >>= 1
            power -= 1
        return res
```
```
class Solution:
    def reverseBits(self, n: int) -> int:
        return int(bin(n)[2:].zfill(32)[::-1], 2)
```
