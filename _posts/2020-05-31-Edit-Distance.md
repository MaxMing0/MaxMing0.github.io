---
layout:     post
title:      LeetCode 72 Edit Distance (Python)
number:     72
level:      Hard
lcurl:      edit-distance
youtube:    okJQqpne4F8
bilibili1:  //player.bilibili.com/player.html?aid=370843412&bvid=BV13Z4y1W7UB&cid=197197201&page=1
xigua:      
date:       2020-05-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given two words word1 and word2, find the minimum number of operations required to convert word1 to word2.

You have the following 3 operations permitted on a word:

1. Insert a character
2. Delete a character
3. Replace a character

### 解题思路

dp[i][j]表示word1前j个字符与word2前i个字符的编辑距离，dp[len(word1)][len(word2)]为所求
```
dp[i][0] = i
dp[0][i] = i
dp[i][j] = dp[i - 1][j - 1] if word2[i - 1] == word1[j - 1]
         = min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]) + 1 else
```

### 代码
```python
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
        l1, l2 = len(word1), len(word2)
        dp1 = [i for i in range(l1 + 1)]
        dp2 = [0] * (l1 + 1)
        for i in range(1, l2 + 1):
            dp2[0] = i
            for j in range(1, l1 + 1):
                if word2[i - 1] == word1[j - 1]:
                    dp2[j] = dp1[j - 1]
                else:
                    dp2[j] = min(dp1[j - 1], dp2[j - 1], dp1[j]) + 1
            dp1 = dp2[:]
        return dp1[-1]
```
