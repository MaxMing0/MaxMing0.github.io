---
layout:     post
title:      LeetCode 326 Power of Three (Python)
number:     326
level:      Easy
lcurl:      power-of-three
youtube:    Sgw9OmYERCU
bilibili1:  //player.bilibili.com/player.html?aid=375304469&bvid=BV1sZ4y1F7Lr&cid=330316901&page=1
xigua:      
date:       2021-04-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an integer n, return true if it is a power of three. Otherwise, return false.

An integer n is a power of three, if there exists an integer x such that n == 3x.

### 解题思路

1. 模3，判断是否为0，如果不是0则必须为1
2. 输入最大3^19,判断是否为3^30约数
3. 取log，判断是否为整数

### 代码
```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        if n == 0:
            return False
        while n % 3 == 0:
            n /= 3
        return n == 1
```
```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        return n > 0 and 3**20 % n == 0
```
```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        if n <= 0:
            return False
        t = math.log(n, 3)
        return math.fabs(t - round(t)) < 0.0000000001
```
