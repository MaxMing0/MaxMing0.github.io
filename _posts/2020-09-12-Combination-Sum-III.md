---
layout:     post
title:      LeetCode 216 Combination Sum III (Python)
number:     216
level:      Medium
lcurl:      combination-sum-iii
youtube:    5ZosFI5oJw8
bilibili1:  //player.bilibili.com/player.html?aid=584619426&bvid=BV1gz4y1Z7CV&cid=234811020&page=1
xigua:      
date:       2020-09-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Backtracking
---

### 题目

Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

Note:

- All numbers will be positive integers.
- The solution set must not contain duplicate combinations.

### 解题思路

回溯，递归的时候需要当前可以放的数，还需要放的数的个数，距离目标还差几，以及临时的结果

### 代码
```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        def dfs(cur, k, n, tmp):
            if k == 0:
                if n == 0:
                    res.append(tmp[:])
                return
            for i in range(cur, 10):
                if i > n:
                    return
                tmp.append(i)
                dfs(i + 1, k - 1, n - i, tmp)
                tmp.pop()

        res = []
        dfs(1, k, n, [])
        return res
```
