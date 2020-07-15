---
layout:     post
title:      LeetCode 151 Reverse Words in a String (Python)
number:     151
level:      Medium
lcurl:      reverse-words-in-a-string
youtube:    3zcL5-7hiek
bilibili1:  //player.bilibili.com/player.html?aid=541293114&bvid=BV1Ei4y1V7yA&cid=212711763&page=1
xigua:      
date:       2020-07-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given an input string, reverse the string word by word.

### 解题思路

1. 对应python直接使用split函数
2. 对于follow up，可以先去掉所有额外的空格，然后使用两个指针将字符串翻转，再对每个单词进行翻转

### 代码
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join(s.split()[::-1])
```
