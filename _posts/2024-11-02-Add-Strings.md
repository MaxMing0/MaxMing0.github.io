---
layout:     post
title:      LeetCode 415 Add Strings (Python)
number:     415
level:      Easy
lcurl:      add-strings
youtube:    
bilibili1:  
xigua:      
date:       2024-11-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2 as a string.

You must solve the problem without using any built-in library for handling large integers (such as BigInteger). You must also not convert the inputs to integers directly.

### 解题思路

推展到n个数的方案，用数组存每个数的长度，每次相加所有数字的最后一位（数的长度），加完之后，长度-1，当所有长度都为0，并且没进位的时候结束

### 代码
```python
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
        nums = [num1, num2]
        n = len(nums)
        l = [len(num) for num in nums]
        c = 0
        res = []
        while any(l) or c:
            for i in range(n):
                if l[i]:
                    l[i] -= 1
                    c += int(nums[i][l[i]])
            res.append(str(c % 10))
            c //= 10
        return "".join(reversed(res))
```
