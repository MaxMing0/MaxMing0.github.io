---
layout:     post
title:      LeetCode 383 Ransom Note (Python)
number:     383
level:      Easy
lcurl:      ransom-note
youtube:    N7Rgmz_RykE
bilibili1:  //player.bilibili.com/player.html?aid=710504577&bvid=BV1GQ4y1N7Q5&cid=186454929&page=1
xigua:      
date:       2020-05-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

### 解题思路

将勒索信和杂志的字符串都转成计数器，遍历勒索信中的每个字母，如果出现的次数都小于杂志中出现的次数则是`True`否则为`False`

### 代码
```python
from collections import Counter
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        ct_ransom = Counter(ransomNote)
        ct_magazine = Counter(magazine)
        for key in ct_ransom:
            if ct_ransom[key] > ct_magazine[key]:
                return False
        return True
```
