---
layout:     post
title:      LeetCode 926 Flip String to Monotone Increasing (Python)
number:     926
level:      Hard
lcurl:      flip-string-to-monotone-increasing
youtube:    z5T8gL3Vplo
bilibili1:  //player.bilibili.com/player.html?aid=207358135&bvid=BV1Vh411i7Wg&cid=386818462&page=1
xigua:      
date:       2021-08-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

A binary string is monotone increasing if it consists of some number of 0's (possibly none), followed by some number of 1's (also possibly none).

You are given a binary string s. You can flip s[i] changing it from 0 to 1 or from 1 to 0.

Return the minimum number of flips to make s monotone increasing.

### 解题思路

方法1：先统计0的总个数，从头开始遍历字符串，如果是0，0的总数-1，如果是1，先用0的个数加1的个数更新结果（假设把前面的数都变成0，后面的都变成1），再把1的个数减一

方法2：
```
dp[i][0]表示s[i]最后为0最少翻转的次数，dp[i][1]表示s[i]最后为1最少翻转的次数
s[i] = 1
dp[i][0] = dp[i - 1][0] + 1
dp[i][1] = min(dp[i - 1][0], dp[i - 1][1])

s[i] = 0
dp[i][0] = dp[i - 1][0]
dp[i][1] = min(dp[i - 1][0] + 1, dp[i - 1][1] + 1)
```

### 代码
```python
class Solution:
    def minFlipsMonoIncr(self, s: str) -> int:
        n = len(s)
        n0 = s.count('0')
        n1 = 0
        res = n - n0
        for i in range(n):
            if s[i] == '0': 
                n0 -= 1
            elif s[i] == '1':
                res = min(res, n1 + n0)
                n1 += 1
        return res
```
```python
class Solution:
    def minFlipsMonoIncr(self, s: str) -> int:
        zero, one = 0, 0
        for c in s:
            if c == '1':
                one, zero = min(zero, one), zero + 1
            else:
                one = min(zero + 1, one + 1)
        return min(zero, one)
```
