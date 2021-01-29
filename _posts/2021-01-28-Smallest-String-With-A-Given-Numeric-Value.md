---
layout:     post
title:      LeetCode 1663 Smallest String With A Given Numeric Value (Python)
number:     1663
level:      Medium
lcurl:      smallest-string-with-a-given-numeric-value
youtube:    9XlhXE4ZFAc
bilibili1:  //player.bilibili.com/player.html?aid=246454170&bvid=BV1gv411e7Ly&cid=289219444&page=1
xigua:      
date:       2021-01-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

The numeric value of a lowercase character is defined as its position (1-indexed) in the alphabet, so the numeric value of a is 1, the numeric value of b is 2, the numeric value of c is 3, and so on.

The numeric value of a string consisting of lowercase characters is defined as the sum of its characters' numeric values. For example, the numeric value of the string "abe" is equal to 1 + 2 + 5 = 8.

You are given two integers n and k. Return the lexicographically smallest string with length equal to n and numeric value equal to k.

Note that a string x is lexicographically smaller than string y if x comes before y in dictionary order, that is, either x is a prefix of y, or if i is the first position such that x[i] != y[i], then x[i] comes before y[i] in alphabetic order.

### 解题思路

贪心，前面都放a，后面都放z，z的个数是`(k-n)/25`

### 代码
```python
class Solution:
    def getSmallestString(self, n: int, k: int) -> str:
        d, m = divmod(k - n, 25)
        return "a" * (n - 1 - d) + (chr(m + 97) if d != n else "") + "z" * d
```
