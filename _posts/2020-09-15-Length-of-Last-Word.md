---
layout:     post
title:      LeetCode 58 Length of Last Word (Python)
number:     58
level:      Easy
lcurl:      length-of-last-word
youtube:    wnqyGLJo-vU
bilibili1:  //player.bilibili.com/player.html?aid=797102422&bvid=BV1ay4y1y7d2&cid=235565643&page=1
xigua:      
date:       2020-09-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word (last word means the last appearing word if we loop from left to right) in the string.

If the last word does not exist, return 0.

Note: A word is defined as a maximal substring consisting of non-space characters only.

### 解题思路

先strip，如果strip完是空，则返回0，否则返回split之后最后一部分的长度

### 代码
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        s = s.strip()
        return len(s.split()[-1]) if s else 0
```
