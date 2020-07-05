---
layout:     post
title:      LeetCode 461 Hamming Distance (Python)
number:     461
level:      Easy
lcurl:      hamming-distance
youtube:    https://youtu.be/5X8URNMREaE
bilibili1:  //player.bilibili.com/player.html?aid=456131849&bvid=BV1M5411Y79g&cid=209107640&page=1
xigua:      
date:       2020-07-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

### 解题思路

对两个数求异或，然后求结果的二进制中一共有多少个1

### 代码
```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        tmp = x ^ y
        res = 0
        while tmp > 0:
            res += tmp & 1
            tmp >>= 1
        return res
```
```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return bin(x ^ y).count('1')
```
