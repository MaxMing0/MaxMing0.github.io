---
layout:     post
title:      LeetCode 409 Longest Palindrome (Python)
number:     409
level:      Easy
lcurl:      longest-palindrome
youtube:    DJJbgeJBIGc
bilibili1:  //player.bilibili.com/player.html?aid=796666780&bvid=BV19C4y1479a&cid=224315291&page=1
xigua:      
date:       2020-08-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
---

### 题目

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

### 解题思路

如果一个字母出现偶数次，则都可以用，奇数次，则可以用次数-1，然后最中间放一个出现奇数次的字母

### 代码
```python
class Solution:
    def longestPalindrome(self, s: str) -> int:
        ct = Counter(s)
        res = 0
        f = 0
        for v in ct.values():
            if v % 2 == 0:
                res += v
            else:
                res += v - 1
                f = 1
        return res + f
```
