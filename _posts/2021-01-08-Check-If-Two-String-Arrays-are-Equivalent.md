---
layout:     post
title:      LeetCode 1662 Check If Two String Arrays are Equivalent (Python)
number:     1662
level:      Easy
lcurl:      check-if-two-string-arrays-are-equivalent
youtube:    lrBuHcHnRws
bilibili1:  //player.bilibili.com/player.html?aid=416111913&bvid=BV1LV411t7v4&cid=279753315&page=1
xigua:      
date:       2020-01-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given two string arrays word1 and word2, return true if the two arrays represent the same string, and false otherwise.

A string is represented by an array if the array elements concatenated in order forms the string.

### 解题思路

将两个数组join到一起进行比较

### 代码
```python
class Solution:
    def arrayStringsAreEqual(self, word1: List[str], word2: List[str]) -> bool:
        return ''.join(word1) == ''.join(word2)
```
