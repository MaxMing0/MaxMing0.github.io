---
layout:     post
title:      LeetCode 1461 Check If a String Contains All Binary Codes of Size K (Python)
number:     1461
level:      Medium
lcurl:      check-if-a-string-contains-all-binary-codes-of-size-k
youtube:    wU5jaC_NCjI
bilibili1:  //player.bilibili.com/player.html?aid=672117217&bvid=BV1oU4y1p7Tr&cid=309285901&page=1
xigua:      
date:       2021-03-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a binary string s and an integer k.

Return True if every binary code of length k is a substring of s. Otherwise, return False.

### 解题思路

取出所有长度为k的子串，放到一个集合里，判断是否大小为2^k

### 代码
```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        return len({s[i:i + k] for i in range(len(s)-k+1)}) == 2 ** k
```
