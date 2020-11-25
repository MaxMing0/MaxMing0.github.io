---
layout:     post
title:      LeetCode 1015 Smallest Integer Divisible by K (Python)
number:     1015
level:      Medium
lcurl:      smallest-integer-divisible-by-k
youtube:    xTOq7qG7EtM
bilibili1:  //player.bilibili.com/player.html?aid=372898230&bvid=BV1PZ4y1G7iU&cid=259611073&page=1
xigua:      
date:       2020-11-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given a positive integer K, you need to find the length of the smallest positive integer N such that N is divisible by K, and N only contains the digit 1.

Return the length of N. If there is no such N, return -1.

Note: N may not fit in a 64-bit signed integer.

### 解题思路

只有当K是2或5的倍数时，才不会被K整除，其他情况遍历整个数列进行判断，具体证明请见视频

### 代码
```python
class Solution:
    def smallestRepunitDivByK(self, K: int) -> int:
        if K % 2 == 0 or K % 5 == 0:
            return -1
        cur, res = 0, 1
        while True:
            cur = (10 * cur + 1) % K
            if cur == 0:
                return res
            res += 1
```
