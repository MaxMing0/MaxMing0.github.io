---
layout:     post
title:      LeetCode 633 Sum of Square Numbers (Python)
number:     633
level:      Medium
lcurl:      sum-of-square-numbers
youtube:    gxh2dYU30RE
bilibili1:  //player.bilibili.com/player.html?aid=207511653&bvid=BV1Qh411i7Yh&cid=397049038&page=1
xigua:      
date:       2021-08-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given a non-negative integer c, decide whether there're two integers a and b such that a^2 + b^2 = c

### 解题思路

使用左右两个指针0和sqrt(c)，求两个数的平方和，如果小于c，left+1，大于c，right+1

### 代码
```python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        left, right = 0, int(c**0.5)
        while left <= right:
            cur = left * left + right * right
            if cur < c:
                left += 1
            elif cur > c:
                right -= 1
            else:
                return True
        return False
```
