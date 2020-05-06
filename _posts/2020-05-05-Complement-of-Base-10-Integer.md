---
layout:     post
title:      LeetCode 1009 Complement of Base 10 Integer (Python)
number:     1009
level:      Easy
lcurl:      complement-of-base-10-integer
youtube:    WCw5DUqo7e4
bilibili1:  //player.bilibili.com/player.html?aid=838059168&bvid=BV1Lg4y167NB&cid=186896724&page=1
xigua:      
date:       2020-05-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---
###此题与476 Number Complement 完全相同

### 题目

Every non-negative integer N has a binary representation.  For example, 5 can be represented as "101" in binary, 11 as "1011" in binary, and so on.  Note that except for N = 0, there are no leading zeroes in any binary representation.

The complement of a binary representation is the number in binary you get when changing every 1 to a 0 and 0 to a 1.  For example, the complement of "101" in binary is "010" in binary.

For a given number N in base-10, return the complement of it's binary representation as a base-10 integer.

### 解题思路

对应一个n位数m，最后的结果为`(2**n - 1) ^ m` （2的n次幂减一的结果异或m）

### 代码
```python
class Solution:
    def findComplement(self, num: int) -> int:
        x = 1
        while x <= num:
            x <<= 1
        return (x - 1) ^ num
```
