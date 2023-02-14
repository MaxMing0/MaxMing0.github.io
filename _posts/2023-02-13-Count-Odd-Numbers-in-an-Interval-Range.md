---
layout:     post
title:      LeetCode 1523 Count Odd Numbers in an Interval Range (Python)
number:     1523
level:      Easy
lcurl:      count-odd-numbers-in-an-interval-range
youtube:    mK9aO9xEdyo
bilibili1:  
xigua:      
date:       2023-02-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given two non-negative integers low and high. Return the count of odd numbers between low and high (inclusive).

### 解题思路

`(high-low)/2`对于`low`和`high`四种不同的奇偶性，只有都是偶数的时候不需要+1

### 代码
```python
class Solution:
    def countOdds(self, low: int, high: int) -> int:
        return (high - low) // 2 + (low % 2 == 1 or high % 2 == 1)
```
