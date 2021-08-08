---
layout:     post
title:      LeetCode 132 Palindrome Partitioning II (Python)
number:     132
level:      Hard
lcurl:      palindrome-partitioning-ii
youtube:    A1H5YpRY7NE
bilibili1:  //player.bilibili.com/player.html?aid=974748203&bvid=BV1944y1C71s&cid=384736933&page=1
xigua:      
date:       2021-08-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a string s, partition s such that every substring of the partition is a palindrome.

Return the minimum cuts needed for a palindrome partitioning of s.

### 解题思路

方法1
```
dp[i]表示s[:i+1]最少的分割次数，dp[n - 1]为所求
dp[i] = min{dp[j]} + 1, s[j + 1: i]为回文字符串
dp[i] = 0, if s[:i]为回文字符串

is_pal[i, j]表示s[i:j]是否为回文字符串
is_pal[i, i] = True
is_pal[i, j] = s[i] == s[j] and is_pal[i + 1, j - 1]
```

方法2
```
cut[i]表示，s[:i]最少的分割次数，cut[n]为结果
初始化cut[i] = i - 1, 把字符串分割成单个字符
枚举字符串的每个位置作为回文字符串的中点，再枚举回文字符串的初始位置以及回文串长度的奇偶性
如果s[i-j:i+j]是回文字符串，cut[i+j] = cur[i-j] + 1
```

### 代码
```python
class Solution:
    def minCut(self, s: str) -> int:
        n = len(s)
        is_pal = [[True] * n for _ in range(n)]

        for i in range(n - 1, -1, -1):
            for j in range(i + 1, n):
                is_pal[i][j] = (s[i] == s[j]) and is_pal[i + 1][j - 1]

        dp = [n] * n
        for i in range(n):
            if is_pal[0][i]:
                dp[i] = 0
                continue
            for j in range(i):
                if is_pal[j + 1][i]:
                    dp[i] = min(dp[i], dp[j] + 1)

        return dp[n - 1]
```

```python
class Solution:
    def minCut(self, s: str) -> int:
        n = len(s)
        cut = [i - 1 for i in range(n + 1)]
        for i in range(n):
            j = 0
            while i - j >= 0 and i + j < n and s[i - j] == s[i + j]:
                cut[i + j + 1] = min(cut[i + j + 1], 1 + cut[i - j])
                j += 1
            j = 1
            while i - j + 1 >= 0 and i + j < n and s[i - j + 1] == s[i + j]:
                cut[i + j + 1] = min(cut[i + j + 1], 1 + cut[i - j + 1])
                j += 1
        return cut[n]
```
