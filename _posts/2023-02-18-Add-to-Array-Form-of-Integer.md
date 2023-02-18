---
layout:     post
title:      LeetCode 989 Add to Array-Form of Integer (Python)
number:     989
level:      Easy
lcurl:      add-to-array-form-of-integer
youtube:    jA89Rf3wndw
bilibili1:  
xigua:      
date:       2023-02-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

The array-form of an integer num is an array representing its digits in left to right order.

For example, for num = 1321, the array form is [1,3,2,1].
Given num, the array-form of an integer, and an integer k, return the array-form of the integer num + k.

### 解题思路

把k加到num最后一位，向前遍历进位，如果还有没进位完的，需要在最后处理进位

### 代码
```python
class Solution:
    def addToArrayForm(self, num: List[int], k: int) -> List[int]:
        num[-1] += k
        for i in range(len(num) - 1, -1, -1):
            carry, num[i] = divmod(num[i], 10)
            if carry == 0:
                break
            if i: 
                num[i - 1] += carry
        if carry:
            num = list(map(int, str(carry))) + num
        return num
```
