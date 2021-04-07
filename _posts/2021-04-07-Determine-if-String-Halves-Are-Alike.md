---
layout:     post
title:      LeetCode 1704 Determine if String Halves Are Alike (Python)
number:     1704
level:      Medium
lcurl:      determine-if-string-halves-are-alike
youtube:    x-Rsx_0VJfc
bilibili1:  //player.bilibili.com/player.html?aid=332418718&bvid=BV1WA41157sf&cid=321004796&page=1
xigua:      
date:       2021-04-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given a string s of even length. Split this string into two halves of equal lengths, and let a be the first half and b be the second half.

Two strings are alike if they have the same number of vowels ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'). Notice that s contains uppercase and lowercase letters.

Return true if a and b are alike. Otherwise, return false.

### 解题思路

将字符串分成两个部分，然后统计元音字母出现的次数，判断是否相等

### 代码
```python
class Solution:
    def halvesAreAlike(self, s: str) -> bool:
        l = len(s) // 2
        ct1 = Counter(s[:l].lower())
        ct2 = Counter(s[l:].lower())
        tmp1 = tmp2 = 0
        for c in ('a', 'e', 'i', 'o', 'u'):
            tmp1 += ct1[c]
            tmp2 += ct2[c]
        return tmp1 == tmp2
```
