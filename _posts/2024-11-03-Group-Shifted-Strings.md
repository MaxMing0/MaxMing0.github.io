---
layout:     post
title:      LeetCode 249 Group Shifted Strings (Python)
number:     249
level:      Medium
lcurl:      group-shifted-strings
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
---

### 题目

Perform the following shift operations on a string:

- Right shift: Replace every letter with the successive letter of the English alphabet, where 'z' is replaced by 'a'. For example, "abc" can be right-shifted to "bcd" or "xyz" can be right-shifted to "yza".
- Left shift: Replace every letter with the preceding letter of the English alphabet, where 'a' is replaced by 'z'. For example, "bcd" can be left-shifted to "abc" or "yza" can be left-shifted to "xyz".
We can keep shifting the string in both directions to form an endless shifting sequence.

- For example, shift "abc" to form the sequence: ... <-> "abc" <-> "bcd" <-> ... <-> "xyz" <-> "yza" <-> .... <-> "zab" <-> "abc" <-> ...
You are given an array of strings strings, group together all strings[i] that belong to the same shifting sequence. You may return the answer in any order.

### 解题思路

不论如何shift，相邻两个字母之间的差值都是定的，求出所有字符串字母之间的差值，作为key，key相同的字符串为一组

### 代码
```python
class Solution:
    def groupStrings(self, strings: List[str]) -> List[List[str]]:
        def get_key(s):
            key = ""
            for a, b in zip(s, s[1:]):
                key += chr((ord(b) - ord(a)) % 26)
            return key
        
        group = defaultdict(list)
        for s in strings:
            key = get_key(s)
            group[key].append(s)
        return list(group.values())
```
