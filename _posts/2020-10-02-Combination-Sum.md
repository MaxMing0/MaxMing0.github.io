---
layout:     post
title:      LeetCode 39 Combination Sum (Python)
number:     39
level:      Medium
lcurl:      combination-sum
youtube:    mzWGosnoBkc
bilibili1:  //player.bilibili.com/player.html?aid=372345893&bvid=BV12Z4y157nE&cid=241275848&page=1
xigua:      
date:       2020-10-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - backtracking
---

### 题目

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

### 解题思路

递归，先把所有的candidate进行排序，这样递归的时候，一旦当前数字大于剩余target，就可以退出，而且每次只能加入大于等于之前的数，来解决去重问题

### 代码
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def dfs(cur, path):
            if cur == 0:
                res.append(path)
            for n in candidates:
                if n > cur:
                    break
                if path and n < path[-1]:
                    continue
                dfs(cur - n, path + [n])
                
        res = []
        candidates.sort()
        dfs(target, [])
        return res
```
