---
layout:     post
title:      LeetCode 1657 Determine if Two Strings Are Close (Python)
number:     1657
level:      Medium
lcurl:      determine-if-two-strings-are-close
youtube:    I0I-KugGj1c
bilibili1:  //player.bilibili.com/player.html?aid=586264761&bvid=BV18z4y1S779&cid=286134981&page=1
xigua:      
date:       2021-01-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Two strings are considered close if you can attain one from the other using the following operations:

- Operation 1: Swap any two existing characters.
  - For example, abcde -> aecdb
- Operation 2: Transform every occurrence of one existing character into another existing character, and do the same with the other character.
  - For example, aacabb -> bbcbaa (all a's turn into b's, and all b's turn into a's)
You can use the operations on either string as many times as necessary.

Given two strings, word1 and word2, return true if word1 and word2 are close, and false otherwise.

### 解题思路

首先判断两个字符串所包含的字符是否相同，在判断所有字符出现的次数的频率是否相同

### 代码
```python
class Solution:
    def closeStrings(self, word1: str, word2: str) -> bool:
        return set(word1) == set(word2) and Counter(Counter(word1).values()) == Counter(Counter(word2).values())
```
