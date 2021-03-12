---
layout:     post
title:      LeetCode 12 Integer to Roman (Python)
number:     12
level:      Medium
lcurl:      integer-to-roman
youtube:    MvpTqAOz3QI
bilibili1:  //player.bilibili.com/player.html?aid=502048026&bvid=BV1hN411Q7ka&cid=309131090&page=1
xigua:      
date:       2021-03-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

- I can be placed before V (5) and X (10) to make 4 and 9. 
- X can be placed before L (50) and C (100) to make 40 and 90. 
- C can be placed before D (500) and M (1000) to make 400 and 900.
Given an integer, convert it to a roman numeral.

### 解题思路

从大到小一次相加，1000-M, 900-CM, 500-D, 400-CD ...

### 代码
```python
class Solution:
    def intToRoman(self, num: int) -> str:
        res = ""
        while num >= 1000:
            res += "M"
            num -= 1000
        while num >= 900:
            res += "CM"
            num -= 900
        while num >= 500:
            res += "D"
            num -= 500
        while num >= 400:
            res += "CD"
            num -= 400
        while num >= 100:
            res += "C"
            num -= 100
        while num >= 90:
            res += "XC"
            num -= 90
        while num >= 50:
            res += "L"
            num -= 50
        while num >= 40:
            res += "XL"
            num -= 40
        while num >= 10:
            res += "X"
            num -= 10
        while num >= 9:
            res += "IX"
            num -= 9
        while num >= 5:
            res += "V"
            num -= 5
        while num >= 4:
            res += "IV"
            num -= 4
        while num >= 1:
            res += "I"
            num -= 1
        return res
```
