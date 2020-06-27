---
layout:     post
title:      LeetCode 279 Perfect Squares (Python)
number:     279
level:      Medium
lcurl:      perfect-squares
youtube:    a7AjjNa0iHM
bilibili1:  //player.bilibili.com/player.html?aid=456239294&bvid=BV1r5411Y7MH&cid=206613672&page=1
xigua:      
date:       2020-06-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
    - BFS
    - Math
---

### 题目

Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

### 解题思路

1. DP dp[n] = min(dp[n-k]) + 1 k is square numbre
2. BSF, 从n开始，拆出完全平方数，直到剩下的数是一个完全平方数结束
3. 数学方法

### 代码
```python
class Solution:
    def numSquares(self, n: int) -> int:
        square_nums = [i**2 for i in range(1, int(math.sqrt(n)) + 1)]
        dp = [float('inf')] * (n + 1)
        dp[0] = 0
        for i in range(1, n+1):
            for square in square_nums:
                if i < square:
                    break
                dp[i] = min(dp[i], dp[i - square] + 1)
        return dp[-1]
```
```python
class Solution:
    def numSquares(self, n: int) -> int:
        square_nums = [i**2 for i in range(1, int(math.sqrt(n)) + 1)]
        level = 0
        queue = {n}
        while queue:
            level += 1
            tmp = set()
            for num in queue:
                for sq in square_nums:    
                    if num == sq:
                        return level
                    elif num < sq:
                        break
                    else:
                        tmp.add(num - sq)
            queue = tmp
```
```python
class Solution:
    def numSquares(self, n: int) -> int:
        def check(n):
            return (math.sqrt(n) - int(math.sqrt(n)) < 0.00000001)
            
        if check(n):
            return 1
        while n % 4 == 0:
            n /= 4
        if (n - 7) % 8 == 0:
            return 4
        for i in range(int(math.sqrt(n))):
            if check(n-(i+1)*(i+1)):
                return 2
        return 3
```
