---
layout:     post
title:      LeetCode 1441 Build an Array With Stack Operations (Python)
number:     1441
level:      Easy
lcurl:      build-an-array-with-stack-operations
youtube:    gee8Ce-lUzo
bilibili1:  //player.bilibili.com/player.html?aid=838017138&bvid=BV1Gg4y167ZD&cid=189631033&page=1
xigua:      
date:       2020-05-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given an array target and an integer n. In each iteration, you will read a number from  list = {1,2,3..., n}.

Build the target array using the following operations:

- Push: Read a new element from the beginning list, and push it in the array.
- Pop: delete the last element of the array.
- If the target array is already built, stop reading more elements.

You are guaranteed that the target array is strictly increasing, only containing numbers between 1 to n inclusive.

Return the operations to build the target array.

You are guaranteed that the answer is unique.

### 解题思路

遍历1到n中的每个数，如果这个数在target中出现，就加一个`Push`,否则加一个`Push`和`Pop`，如果target数组已经遍历完了，就退出循环

### 代码
```python
class Solution:
    def buildArray(self, target, n: int):
        res = []
        p = 0
        for i in range(1, n + 1):
            if target[p] == i:
                res.append("Push")
                p += 1
            else:
                res.append("Push")
                res.append("Pop")
            if p == len(target):
                break
        return res
```
