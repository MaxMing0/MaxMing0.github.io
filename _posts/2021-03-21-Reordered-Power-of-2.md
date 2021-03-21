---
layout:     post
title:      LeetCode 869 Reordered Power of 2 (Python)
number:     869
level:      Medium
lcurl:      reordered-power-of-2
youtube:    nyMEJ4lLp8Y
bilibili1:  //player.bilibili.com/player.html?aid=757128855&bvid=BV1M64y1D78v&cid=313344253&page=1
xigua:      
date:       2021-03-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Starting with a positive integer N, we reorder the digits in any order (including the original order) such that the leading digit is not zero.

Return true if and only if we can do this in a way such that the resulting number is a power of 2.

### 解题思路

降所有2的幂转换成字符串然后排序，对N排序，判断是否在2的幂中

### 代码
```python
class Solution:
    def reorderedPowerOf2(self, N: int) -> bool:
        pow2 = [''.join(sorted(list(str(2**i)))) for i in range(31)]
        return ''.join(sorted(list(str(N)))) in pow2
```
