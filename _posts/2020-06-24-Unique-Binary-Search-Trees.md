---
layout:     post
title:      LeetCode 96 Unique Binary Search Trees (Python)
number:     96
level:      Medium
lcurl:      unique-binary-search-trees
youtube:    wQPOcmtTkhI
bilibili1:  //player.bilibili.com/player.html?aid=456034738&bvid=BV1e5411W72t&cid=205237022&page=1
xigua:      
date:       2020-06-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?

### 解题思路

1. 如果确定了根，那么就确定了左右子树有哪些节点，那么就可以简化成两个子树的BST的个数相乘，再枚举每个数作为根
2. 这个过程的结果就是[卡特兰数](https://zh.wikipedia.org/zh-hans/%E5%8D%A1%E5%A1%94%E5%85%B0%E6%95%B0)的第n项

### 代码
```python
class Solution:
    def numTrees(self, n: int) -> int:
        res = [0] * (n + 1)
        res[0] = res[1] = 1
        for i in range(2, n + 1):
            tmp = 0
            for j in range(0, i):
                tmp += res[j] * res[i - 1 - j]
            res[i] = tmp
        return res[n]
```
```python
class Solution:
    def numTrees(self, n: int) -> int:
        C = 1
        for i in range(n):
            C = C * 2 * (2 * i + 1) // (i + 2)
        return C
```
