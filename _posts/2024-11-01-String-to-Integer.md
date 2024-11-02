---
layout:     post
title:      LeetCode 8 String to Integer (atoi) (Python)
number:     8
level:      Medium
lcurl:      string-to-integer-atoi
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer.

The algorithm for myAtoi(string s) is as follows:

1. Whitespace: Ignore any leading whitespace (" ").
2. Signedness: Determine the sign by checking if the next character is '-' or '+', assuming positivity if neither present.
3. Conversion: Read the integer by skipping leading zeros until a non-digit character is encountered or the end of the string is reached. If no digits were read, then the result is 0.
4. Rounding: If the integer is out of the 32-bit signed integer range [-231, 231 - 1], then round the integer to remain in the range. Specifically, integers less than -231 should be rounded to -231, and integers greater than 231 - 1 should be rounded to 231 - 1.
Return the integer as the final result.

### 解题思路

先判断正负，之后遍历数字，如果超过范围则返回最大/小值

### 代码
```python
class Solution:
    def myAtoi(self, s: str) -> int:
        s = s.strip()
        if len(s) == 0:
            return 0
        INT_MAX = 2147483647
        INT_MIN = -2147483648
        flag = 1
        if s[0] == '-':
            flag = -1
            s = s[1:]
        elif s[0] == '+':
            s = s[1:]
        res = 0
        for c in s:
            if not c.isdigit():
                break
            res *= 10
            res += ord(c) - ord('0')
            if flag == 1:
                if res > 2147483647:
                    return INT_MAX
            else:
                if res > 2147483648:
                    return INT_MIN
        return res * flag
```
