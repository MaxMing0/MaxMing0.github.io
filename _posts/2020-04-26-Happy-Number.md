---
layout:     post
title:      LeetCode 202 Happy Number (Python)
number:     202
level:      Easy
lcurl:      happy-number
youtube:    c4AtZv9PMZ0
bilibili1:  //player.bilibili.com/player.html?aid=327544547&bvid=BV1CA41187LQ&cid=173332435&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - Hash Table
    - Math
---

### 题目

Write an algorithm to determine if a number n is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Return True if n is a happy number, and False if not.

### 解题思路



### 代码
```python
class Solution:
    def isHappy(self, n: int) -> bool:
        s = {n}
        while n != 1:
            tmp = sum([int(c) ** 2 for c in str(n)])
            if tmp in s:
                return False
            s.add(tmp)
            n = tmp
        return True
```