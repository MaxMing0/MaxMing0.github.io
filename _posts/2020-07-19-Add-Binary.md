---
layout:     post
title:      LeetCode 67 Add Binary (Python)
number:     67
level:      Easy
lcurl:      add-binary
youtube:    H3pv_vBmOEI
bilibili1:  //player.bilibili.com/player.html?aid=456408838&bvid=BV1Q5411h7gc&cid=214204579&page=1
xigua:      
date:       2020-07-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.

### 解题思路

模拟两个数的加法，维护一个进位

### 代码
```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        def add(x, y, carry):
            s = x + y + carry        
            return (s // 2, s % 2)
    
        ml = max(len(a), len(b))
        res = ''
        carry = 0 
        a = a.rjust(ml, '0')
        b = b.rjust(ml, '0')
        for i in range(ml-1, -1, -1):         
            carry, s = add(int(a[i]), int(b[i]), int(carry))
            res = str(s) + res
        return '1' + res if carry else res
```
