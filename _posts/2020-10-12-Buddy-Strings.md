---
layout:     post
title:      LeetCode 859 Buddy Strings (Python)
number:     859
level:      Easy
lcurl:      buddy-strings
youtube:    paq4KA9nMnw
bilibili1:  //player.bilibili.com/player.html?aid=584979022&bvid=BV1nz4y1o7Wo&cid=244914902&page=1
xigua:      
date:       2020-10-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given two strings A and B of lowercase letters, return true if you can swap two letters in A so the result is equal to B, otherwise, return false.

Swapping letters is defined as taking two indices i and j (0-indexed) such that i != j and swapping the characters at A[i] and A[j]. For example, swapping at indices 0 and 2 in "abcd" results in "cbad".

### 解题思路

分类讨论
1. A和B长度不同，返回false
2. A和B长度相同，而且为相同字符串，如果存在任一个字符出现的次数大于1，返回True
3. A和B长度相同，而且为不同字符串，对应位置组成pair，字母不同的pair数为2，前两个pair相反，返回True

### 代码
```python
class Solution:
    def buddyStrings(self, A: str, B: str) -> bool:
        if len(A) != len(B):
            return False
        if A == B:
            s = set()
            for a in A:
                if a in s:
                    return True
                s.add(a)
            return False
        pair = []
        for a, b in zip(A, B):
            if a != b:
                pair.append((a, b))
            if len(pair) > 2:
                return False
        return len(pair) == 2 and pair[0] == pair[1][::-1]
```
