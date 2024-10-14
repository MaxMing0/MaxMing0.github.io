---
layout:     post
title:      LeetCode 3043 Find the Length of the Longest Common Prefix (Python)
number:     3043
level:      Medium
lcurl:      find-the-length-of-the-longest-common-prefix
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Set
---

### 题目

You are given two arrays with positive integers arr1 and arr2.

A prefix of a positive integer is an integer formed by one or more of its digits, starting from its leftmost digit. For example, 123 is a prefix of the integer 12345, while 234 is not.

A common prefix of two integers a and b is an integer c, such that c is a prefix of both a and b. For example, 5655359 and 56554 have a common prefix 565 while 1223 and 43456 do not have a common prefix.

You need to find the length of the longest common prefix between all pairs of integers (x, y) such that x belongs to arr1 and y belongs to arr2.

Return the length of the longest common prefix among all pairs. If no common prefix exists among them, return 0.

### 解题思路

把第一个数组的所有前缀放到一个数组里，求前缀可以对数字//10

之后遍历所有第二个数组里的数，求出所有前缀，如果出现在set里，就更新结果

### 代码
```python
class Solution:
    def longestCommonPrefix(self, arr1: List[int], arr2: List[int]) -> int:
        prefix = set()
        res = 0
        for n in arr1:
            while n:
                prefix.add(n)
                n //= 10
        for n in arr2:
            while n:
                if n in prefix:
                    res = max(res, len(str(n)))
                    break
                n //= 10
        return res
```
