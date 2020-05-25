---
layout:     post
title:      LeetCode 1035 Uncrossed Lines (Python)
number:     1035
level:      Medium
lcurl:      uncrossed-lines
youtube:    jxPHhLCxGFQ
bilibili1:  //player.bilibili.com/player.html?aid=540805954&bvid=BV1si4y1s79e&cid=195038905&page=1
xigua:      
date:       2020-05-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

We write the integers of A and B (in the order they are given) on two separate horizontal lines.

Now, we may draw connecting lines: a straight line connecting two numbers A[i] and B[j] such that:

- A[i] == B[j];
- The line we draw does not intersect any other connecting (non-horizontal) line.
Note that a connecting lines cannot intersect even at the endpoints: each number can only belong to one connecting line.

Return the maximum number of connecting lines we can draw in this way.

### 解题思路

DP, dp[i][j]表示A数组前i个数和B数组前j个数最多可以练成的线，dp[n][m]为答案
```
dp[i][j] = max dp[i - 1][j]
               dp[i][j - 1]
               1 + dp[i - 1][j - 1] if A[i] == B[j] and i >= 1 and j >= 1
               1                    if A[i] == B[j]
```

### 代码
```python
class Solution:
    def maxUncrossedLines(self, A: List[int], B: List[int]) -> int:
        dp = [[0 for j in range(len(B))] for i in range(len(A))]
        for i, a in enumerate(A):
            for j, b in enumerate(B):
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                if a == b:
                    if i >= 1 and j >= 1:
                        dp[i][j] = max(dp[i][j], 1 + dp[i - 1][j - 1])
                    else:
                        dp[i][j] = max(dp[i][j], 1)
        return dp[len(A) - 1][len(B) - 1]
```
