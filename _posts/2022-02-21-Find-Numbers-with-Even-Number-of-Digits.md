---
layout:     post
title:      LeetCode 1295 Find Numbers with Even Number of Digits (Python)
number:     1295
level:      Easy
lcurl:      find-numbers-with-even-number-of-digits
youtube:    eJthzB67RWo
bilibili1:  
xigua:      
date:       2022-02-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array nums of integers, return how many of them contain an even number of digits.

### 解题思路



### 代码
```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        return sum(len(str(n)) % 2 == 0 for n in nums)
```
```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        res = 0
        for n in nums:
            tmp = 0
            while n > 0:
                tmp += 1
                n //= 10
            if tmp % 2 == 0:
                res += 1

        return res
```
