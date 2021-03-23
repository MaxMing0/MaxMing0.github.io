---
layout:     post
title:      LeetCode 966 Vowel Spellchecker (Python)
number:     966
level:      Medium
lcurl:      vowel-spellchecker
youtube:    TgZEBoqAvXA
bilibili1:  //player.bilibili.com/player.html?aid=887351752&bvid=BV1oK4y1T7kR&cid=314173455&page=1
xigua:      
date:       2021-03-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

Given a wordlist, we want to implement a spellchecker that converts a query word into a correct word.

For a given query word, the spell checker handles two categories of spelling mistakes:

- Capitalization: If the query matches a word in the wordlist (case-insensitive), then the query word is returned with the same case as the case in the wordlist.
  - Example: wordlist = ["yellow"], query = "YellOw": correct = "yellow"
  - Example: wordlist = ["Yellow"], query = "yellow": correct = "Yellow"
  - Example: wordlist = ["yellow"], query = "yellow": correct = "yellow"
- Vowel Errors: If after replacing the vowels ('a', 'e', 'i', 'o', 'u') of the query word with any vowel individually, it matches a word in the wordlist (case-insensitive), then the query word is returned with the same case as the match in the wordlist.
  - Example: wordlist = ["YellOw"], query = "yollow": correct = "YellOw"
  - Example: wordlist = ["YellOw"], query = "yeellow": correct = "" (no match)
  - Example: wordlist = ["YellOw"], query = "yllw": correct = "" (no match)
In addition, the spell checker operates under the following precedence rules:

- When the query exactly matches a word in the wordlist (case-sensitive), you should return the same word back.
- When the query matches a word up to capitlization, you should return the first such match in the wordlist.
- When the query matches a word up to vowel errors, you should return the first such match in the wordlist.
- If the query has no matches in the wordlist, you should return the empty string.
Given some queries, return a list of words answer, where answer[i] is the correct word for query = queries[i].

### 解题思路

使用两个字典存变成小写以及替换所有元音字母后的形式（把所有元音字母变成`#`）

### 代码
```python
class Solution:
    def spellchecker(self, wordlist: List[str], queries: List[str]) -> List[str]:
        wordset = set(wordlist)
        capdict = {}
        voweldict = {}
        for w in wordlist:
            lower = w.lower()
            if lower not in capdict:
                capdict[lower] = w
            tmp = ''.join(['#' if c in 'aeiou' else c for c in lower])
            if tmp not in voweldict:
                voweldict[tmp] = w
        res = []
        for q in queries:
            if q in wordset:
                res.append(q)
                continue
            lower = q.lower()
            if lower in capdict:
                res.append(capdict[lower])
                continue
            tmp = ''.join(['#' if c in 'aeiou' else c for c in lower])
            if tmp in voweldict:
                res.append(voweldict[tmp])
                continue
            res.append("")
        return res
```
