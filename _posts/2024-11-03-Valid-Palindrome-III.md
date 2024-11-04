---
layout:     post
title:      LeetCode 1216 Valid Palindrome III (Python)
number:     1216
level:      Hard
lcurl:      valid-palindrome-iii/
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a string s and an integer k, return true if s is a k-palindrome.

A string is k-palindrome if it can be transformed into a palindrome by removing at most k characters from it.

### 解题思路

dp[i][j]表示从i到j需要删除多少个字符才是回文，所求为dp[0][n-1] <= k
```
dp[i][j] = 0 if i == j (只有一个字符)
         = 1 or 0 if i == j - 1 (只有两个字符，相同为0，不同为1)
         = dp[i+1][j-1] if s[i]==s[j]
         = 1 + min(dp[i + 1][j], dp[i][j - 1]) if s[i] != s[j]
```

### 代码
```python
class Solution:
    def isValidPalindrome(self, s: str, k: int) -> bool:
        def dp(s, i, j):
            if i == j:
                return 0
            if i == j - 1:
                return 0 if s[i] == s[j] else 1
            if m[i][j] != -1:
                return m[i][j]
            if s[i] == s[j]:
                m[i][j] = dp(s, i + 1, j - 1)
                return m[i][j]
            m[i][j] = 1 + min(dp(s, i + 1, j), dp(s, i, j - 1))
            return m[i][j]

        n = len(s)
        m = [[-1] * n for i in range(n)]
        return dp(s, 0, n - 1) <= k

class Solution:
    def isValidPalindrome(self, s: str, k: int) -> bool:
        n = len(s)
        m = [[0] * n for i in range(n)]
        for i in range(n - 2, -1, -1):
            for j in range(i + 1, n):
                if s[i] == s[j]:
                    m[i][j] = m[i + 1][j - 1]
                else:
                    m[i][j] = 1 + min(m[i + 1][j], m[i][j - 1])
        return m[0][n - 1] <= k
```
