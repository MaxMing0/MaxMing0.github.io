---
layout:     post
title:      LeetCode 140 Word Break II (Python)
number:     140
level:      Hard
lcurl:      word-break-ii
youtube:    wSGIQW0uaeo
bilibili1:  //player.bilibili.com/player.html?aid=626508726&bvid=BV1ht4y1X7DJ&cid=218365272&page=1
xigua:      
date:       2020-07-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.

Note:

- The same word in the dictionary may be reused multiple times in the segmentation.
- You may assume the dictionary does not contain duplicate words.

### 解题思路

DFS枚举每次切单词的位置，优化是使用Memorization，这样每个字符串只用求一遍

### 代码
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
        def dfs(i):
            if i in memo:
                return memo[i]
            res = []
            for j in range(i, len(s)):
                prefix = s[i: j + 1]
                if prefix in wordDict:
                    tmp = dfs(j + 1)
                    for word in tmp:
                        res.append((prefix + " " + word).strip())
            memo[i] = res
            return res
        
        wordDict = set(wordDict)
        memo = {len(s): [""]}
        return dfs(0)
```
