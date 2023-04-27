---
layout:     post
title:      LeetCode 1416 Restore The Array (Python)
number:     1416
level:      Hard
lcurl:      restore-the-array
youtube:    YG7FBW3gc8k
bilibili1:  
xigua:      
date:       2023-04-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

A program was supposed to print an array of integers. The program forgot to print whitespaces and the array is printed as a string of digits s and all we know is that all integers in the array were in the range [1, k] and there are no leading zeros in the array.

Given the string s and the integer k, return the number of the possible arrays that can be printed as s using the mentioned program. Since the answer may be very large, return it modulo 109 + 7.

### 解题思路
```
dp[i] 表示从第i位到最后一位可以构成可能数组的个数，dp[0]为所求
dp[n] = 1
dp[i] = sum(dp[j + 1]) s[i: j + 1] <= k
      = 0 if s[i] == '0'
eg. s = "1017" k = 200
dp[4] = 1
dp[3] = dp[4] (7) = 1
dp[2] = dp[3](1) + dp[4](17) = 2
dp[1] = 0
dp[0] = dp[1](1) + dp[2](10) + dp[3](101) = 3
```

### 代码
```python
class Solution:
    def numberOfArrays(self, s: str, k: int) -> int:
        n = len(s)
        dp = [0] * (n + 1)
        dp[-1] = 1
        MOD = 10 ** 9 + 7
        for i in range(n - 1, -1, -1):
            if s[i] == '0':
                continue
            num = 0
            j = i
            while j < n and int(s[i: j + 1]) <= k:
                num += dp[j + 1]
                j += 1
            dp[i] = num % MOD
        print(dp)
        return dp[0]
```
