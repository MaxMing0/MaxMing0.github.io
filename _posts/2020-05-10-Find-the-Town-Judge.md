---
layout:     post
title:      LeetCode 997 Find the Town Judge (Python)
number:     997
level:      Easy
lcurl:      find-the-town-judge
youtube:    qhFHaLPjfjM
bilibili1:  
xigua:      
date:       2020-05-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

In a town, there are N people labelled from 1 to N.  There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

1. The town judge trusts nobody.
2. Everybody (except for the town judge) trusts the town judge.
3. There is exactly one person that satisfies properties 1 and 2.

You are given trust, an array of pairs trust[i] = [a, b] representing that the person labelled a trusts the person labelled b.

If the town judge exists and can be identified, return the label of the town judge.  Otherwise, return -1.

### 解题思路

对于法官，他的入度是N - 1，出度是0，或者入度与出度的差是N - 1

### 代码
```python
class Solution:
    def findJudge(self, N: int, trust: List[List[int]]) -> int:
        ct = [0] * (N + 1)
        for x, y in trust:
            ct[x] -= 1
            ct[y] += 1
        for i in range(1, N + 1):
            if ct[i] == N - 1:
                return i
        return -1
```
