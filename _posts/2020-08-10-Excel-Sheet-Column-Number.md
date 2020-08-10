---
layout:     post
title:      LeetCode 171 Excel Sheet Column Number (Python)
number:     171
level:      Easy
lcurl:      excel-sheet-column-number
youtube:    tTwvIF4i9Hk
bilibili1:  //player.bilibili.com/player.html?aid=456669049&bvid=BV1h541187Sv&cid=222715152&page=1
xigua:      
date:       2020-08-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given a column title as appear in an Excel sheet, return its corresponding column number.

### 解题思路

相当于将26进制数转换成10进制数

### 代码
```python
class Solution:
    def titleToNumber(self, s: str) -> int:
        res = 0
        for c in s:
            res = res * 26 + ord(c) - 64
        return res
```
