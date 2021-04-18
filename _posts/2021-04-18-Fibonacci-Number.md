---
layout:     post
title:      LeetCode 509 Fibonacci Number (Python)
number:     509
level:      Easy
lcurl:      fibonacci-number
youtube:    ALNw7dZDwA8
bilibili1:  //player.bilibili.com/player.html?aid=802647520&bvid=BV15y4y147Re&cid=325884218&page=1
xigua:      
date:       2021-04-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,
```
F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
```
Given n, calculate F(n).


### 解题思路

递归或者递推，如果N很大，可以用矩阵倍方的方法

### 代码
```python
class Solution:
    def fib(self, n: int) -> int:
        if n == 0:
            return 0
        if n <= 2:
            return 1
        f1 = f2 = 1
        for i in range(2, n):
            f1, f2 = f2, f1 + f2
        return f2
```
