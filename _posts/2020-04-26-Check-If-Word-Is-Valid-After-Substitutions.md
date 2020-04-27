---
layout:     post
title:      LeetCode 1003 Check If Word Is Valid After Substitutions (Python)
number:     1003
level:      Medium
lcurl:      check-if-word-is-valid-after-substitutions
youtube:    2Zwpd3iPD2Y
bilibili1:  //player.bilibili.com/player.html?aid=412844911&bvid=BV1WV411Z74P&cid=181298984&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
    - Recursion
---

### 题目

We are given that the string "abc" is valid.

From any valid string V, we may split V into two pieces X and Y such that X + Y (X concatenated with Y) is equal to V.  (X or Y may be empty.)  Then, X + "abc" + Y is also valid.

If for example S = "abc", then examples of valid strings are: "abc", "aabcbc", "abcabc", "abcabcababcc".  Examples of invalid strings are: "abccba", "ab", "cababc", "bac".

Return true if and only if the given string S is valid.

### 解题思路



### 代码
```python
class Solution:
    def isValid(self, S: str) -> bool:
        while 'abc' in S:
            S = S.replace("abc", "")
        return not S
```