---
layout:     post
title:      LeetCode 906 Super Palindromes (Python)
number:     906
level:      Hard
lcurl:      super-palindromes
youtube:    Et1YUhyhtiE
bilibili1:  //player.bilibili.com/player.html?aid=332911664&bvid=BV1LA41157Wf&cid=335917643&page=1
xigua:      
date:       2021-05-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Let's say a positive integer is a super-palindrome if it is a palindrome, and it is also the square of a palindrome.

Given two positive integers left and right represented as strings, return the number of super-palindromes integers in the inclusive range [left, right].

### 解题思路

构造回文数，然后判读其平方是否也是回文数，根据题目的数据范围，最大100000能构成题目要求的超级回文数，构造的时候需要构造长度为奇数和偶数

### 代码
```python
class Solution:
    def superpalindromesInRange(self, left: str, right: str) -> int:
        def check(x):
            return str(x) == str(x)[::-1]
        
        left, right = int(left), int(right)
        upper = 100000
        res = 0
        
        for i in range(upper):
            s = str(i)
            t = int(s + s[-2::-1]) ** 2
            if t > right:
                break
            if t >= left and check(t):
                res += 1
                
        for i in range(upper):
            s = str(i)
            t = int(s + s[::-1]) ** 2
            if t > right:
                break
            if t >= left and check(t):
                res += 1
        return res
```
