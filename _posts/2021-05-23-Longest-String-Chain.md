---
layout:     post
title:      LeetCode 1048 Longest String Chain (Python)
number:     1048
level:      Medium
lcurl:      longest-string-chain
youtube:    tHsPLkvKcI8
bilibili1:  //player.bilibili.com/player.html?aid=888200770&bvid=BV17K4y1G7et&cid=343001326&page=1
xigua:      
date:       2021-05-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a list of words, each word consists of English lowercase letters.

Let's say word1 is a predecessor of word2 if and only if we can add exactly one letter anywhere in word1 to make it equal to word2. For example, "abc" is a predecessor of "abac".

A word chain is a sequence of words [word_1, word_2, ..., word_k] with k >= 1, where word_1 is a predecessor of word_2, word_2 is a predecessor of word_3, and so on.

Return the longest possible length of a word chain with words chosen from the given list of words.


### 解题思路

先对所以单词按长度进行排序，对于每一个单词，遍历所有位置，去掉这个字母，判断是否之前出现过，如果出现过，长度加一

### 代码
```python
class Solution:
    def longestStrChain(self, words: List[str]) -> int:
        words.sort(key=lambda word: len(word))
        dic = {}
        res = 0
        for word in words:
            cur = 1
            for i in range(len(word)):
                tmp = word[:i] + word[i + 1:]
                if tmp in dic:
                    cur = max(cur, dic[tmp] + 1)
            dic[word] = cur
            res = max(res, dic[word])
        return res
```
