---
layout:     post
title:      LeetCode 1202 Smallest String With Swaps (Python)
number:     1202
level:      Medium
lcurl:      smallest-string-with-swaps
youtube:    tC3rjpxwFs0
bilibili1:  
xigua:      
date:       20212-02-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

You are given a string s, and an array of pairs of indices in the string pairs where pairs[i] = [a, b] indicates 2 indices(0-indexed) of the string.

You can swap the characters at any pair of indices in the given pairs any number of times.

Return the lexicographically smallest string that s can be changed to after using the swaps.

### 解题思路

通过搜索找到所有可以交换的位置作为一组，然后把对应字母按顺序放入结果中

### 代码
```python
class Solution:
    def smallestStringWithSwaps(self, s: str, pairs: List[List[int]]) -> str:
        edge = defaultdict(list)
        for x, y in pairs:
            edge[x].append(y)
            edge[y].append(x)
        n = len(s)
        res = [""] * n
        visit = set()
        for i in range(n):
            if i in visit:
                continue
            stack = [i]
            visit.add(i)
            char, pos = [], []
            while stack:
                cur = stack.pop()
                pos.append(cur)
                char.append(s[cur])
                for nei in edge[cur]:
                    if nei not in visit:
                        stack.append(nei)
                        visit.add(nei)
            char.sort()
            pos.sort()
            for p, c in zip(pos, char):
                res[p] = c
        return "".join(res)
```
