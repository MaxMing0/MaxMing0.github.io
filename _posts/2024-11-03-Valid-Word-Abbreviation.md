---
layout:     post
title:      LeetCode 408 Valid Word Abbreviation (Python)
number:     408
level:      Easy
lcurl:      valid-word-abbreviation
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

A string can be abbreviated by replacing any number of non-adjacent, non-empty substrings with their lengths. The lengths should not have leading zeros.

For example, a string such as "substitution" could be abbreviated as (but not limited to):

"s10n" ("s ubstitutio n")
"sub4u4" ("sub stit u tion")
"12" ("substitution")
"su3i1u2on" ("su bst i t u ti on")
"substitution" (no substrings replaced)
The following are not valid abbreviations:

"s55n" ("s ubsti tutio n", the replaced substrings are adjacent)
"s010n" (has leading zeros)
"s0ubstitution" (replaces an empty substring)
Given a string word and an abbreviation abbr, return whether the string matches the given abbreviation.

A substring is a contiguous non-empty sequence of characters within a string.

### 解题思路

两个指针指向字符串和缩写，同时向右移动，如果缩写是数字，就记录下来记录当前数字，直到不是数字为止，遇到字母，指向单词的指针向右移动数字位置，判断不能越界且对应的字母相等，最后处理缩写尾部是数字的情况，并且两个指针都到走到最后

### 代码
```python
class Solution:
    def validWordAbbreviation(self, word: str, abbr: str) -> bool:
        m, n = len(word), len(abbr)
        i = j = cur = 0
        while i < m and j < n:
            if abbr[j].isdigit():
                if abbr[j] == "0" and cur == 0:
                    return False
                cur = cur * 10 + int(abbr[j])
            else:
                i += cur
                cur = 0
                if i >= m or word[i] != abbr[j]:
                    return False
                i += 1
            j += 1
        return i + cur == m and j == n
```
