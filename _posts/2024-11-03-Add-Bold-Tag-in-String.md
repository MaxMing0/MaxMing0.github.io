---
layout:     post
title:      LeetCode 616 Add Bold Tag in String (Python)
number:     616
level:      Medium
lcurl:      add-bold-tag-in-string
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

You are given a string s and an array of strings words.

You should add a closed pair of bold tag <b> and </b> to wrap the substrings in s that exist in words.

- If two such substrings overlap, you should wrap them together with only one pair of closed bold-tag.
- If two substrings wrapped by bold tags are consecutive, you should combine them.
Return s after adding the bold tags.

### 解题思路

用一个数组维护所有需要加粗的字母位置，遍历每个单词，用find找到单词match开始的位置i，后面单词长度的位置，都标为true，再从i+1位置继续寻找。最后遍历这个数组，把连续标为True的位置前后加上tag

### 代码
```python
class Solution:
    def addBoldTag(self, s: str, words: List[str]) -> str:
        n = len(s)
        bold = [False] * (n + 1)
        for word in words:
            i = s.find(word)
            while i != -1:
                for j in range(i, i + len(word)):
                    bold[j] = True
                i = s.find(word, i + 1)
        open, close, res = "<b>", "</b>", []
        for i in range(n):
            if bold[i] and not bold[i - 1]:
                res.append(open)
            res.append(s[i])
            if bold[i] and not bold[i + 1]:
                res.append(close)
        return "".join(res)
```
