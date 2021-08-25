---
layout:     post
title:      LeetCode 537 Complex Number Multiplication (Python)
number:     537
level:      Medium
lcurl:      complex-number-multiplication
youtube:    5eZjmZrMjoc
bilibili1:  //player.bilibili.com/player.html?aid=890052522&bvid=BV1sP4y1p7Px&cid=396276483&page=1
xigua:      
date:       2021-08-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

A complex number can be represented as a string on the form "real+imaginaryi" where:

- real is the real part and is an integer in the range [-100, 100].
- imaginary is the imaginary part and is an integer in the range [-100, 100].
- i^2 == -1.
Given two complex numbers num1 and num2 as strings, return a string of the complex number that represents their multiplications.

### 解题思路

先拿到两个数的实部和虚部，求出结果

### 代码
```python
class Solution:
    def complexNumberMultiply(self, num1: str, num2: str) -> str:
        a1, b1 = map(int, num1[:-1].split('+'))
        a2, b2 = map(int, num2[:-1].split('+'))
        return '%d+%di' % (a1 * a2 - b1 * b2, a1 * b2 + a2 * b1)
```
