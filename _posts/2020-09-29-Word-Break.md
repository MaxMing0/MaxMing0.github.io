---
layout:     post
title:      LeetCode 139 Word Break (Python)
number:     139
level:      Medium
lcurl:      word-break
youtube:    ekV_mLCY0ZA
bilibili1:  //player.bilibili.com/player.html?aid=842325878&bvid=BV1p54y1k7vf&cid=240165291&page=1
xigua:      
date:       2020-09-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - dp
---

### 题目

Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

Note:

- The same word in the dictionary may be reused multiple times in the segmentation.
- You may assume the dictionary does not contain duplicate words.

### 解题思路

dp[i]表示字符串s[:i]是否可分的，dp[len(s)]为所求

dp[i] = any(s[i - l: i] == word and dp[i - l], l = len(word))

### 代码
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        n = len(s)
        dp = [False] * (n + 1)
        dp[0] = True
        for i in range(1, n + 1):
            for w in wordDict:
                l = len(w)
                if s[i - l: i] == w and dp[i - l]:
                    dp[i] = True
                    break
        return dp[-1]
```
