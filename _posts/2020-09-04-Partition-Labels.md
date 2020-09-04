---
layout:     post
title:      LeetCode 763 Partition Labels (Python)
number:     763
level:      Medium
lcurl:      partition-labels
youtube:    yqIo2PdN2vA
bilibili1:  //player.bilibili.com/player.html?aid=669379718&bvid=BV1Ca4y177LW&cid=232136101&page=1
xigua:      
date:       2020-09-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

A string S of lowercase English letters is given. We want to partition this string into as many parts as possible so that each letter appears in at most one part, and return a list of integers representing the size of these parts.

### 解题思路

先求出每个字母最后出现的位置，从头开始遍历，更新该段子串至少要包含的位置，如果遍历到了每段的最后一个位置，就在这里进行分割

### 代码
```python
class Solution:
    def partitionLabels(self, S: str) -> List[int]:
        last = {c: i for i, c in enumerate(S)}
        pre = cur = 0
        res = []
        for i, c in enumerate(S):
            cur = max(cur, last[c])
            if i == cur:
                res.append(i - pre + 1)
                pre = i + 1   
        return res
```
