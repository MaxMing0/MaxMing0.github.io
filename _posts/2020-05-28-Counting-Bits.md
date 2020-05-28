---
layout:     post
title:      LeetCode 338 Counting Bits (Python)
number:     338
level:      Medium
lcurl:      counting-bits
youtube:    OfIyDdepVL0
bilibili1:  //player.bilibili.com/player.html?aid=498272026&bvid=BV1VK411s7xi&cid=196019104&page=1
xigua:      
date:       2020-05-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

### 解题思路

对于一个数`i`转换成二进制之后1的个数，如果`i`是偶数，则和`i/2`的个数相同，如果`i`是奇数，则为`i/2`的个数加1

### 代码
```python
class Solution:
    def countBits(self, num: int) -> List[int]:
        res = [0] * (num + 1)
        for i in range(num + 1):
            res[i] = res[i >> 1] + (i & 1)
        return res
```
