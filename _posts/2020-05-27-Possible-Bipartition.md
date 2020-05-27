---
layout:     post
title:      LeetCode 886 Possible Bipartition (Python)
number:     886
level:      Medium
lcurl:      possible-bipartition
youtube:    K97LwvEOxEk
bilibili1:  //player.bilibili.com/player.html?aid=925770904&bvid=BV1FT4y1g77u&cid=195694522&page=1
xigua:      
date:       2020-05-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a set of N people (numbered 1, 2, ..., N), we would like to split everyone into two groups of any size.

Each person may dislike some other people, and they should not go into the same group. 

Formally, if dislikes[i] = [a, b], it means it is not allowed to put the people numbered a and b into the same group.

Return true if and only if it is possible to split everyone into two groups in this way.

### 解题思路

对每个点进行黑白染色（DFS或BFS），如果发现冲突则返回False

### 代码
```python
class Solution:
    def possibleBipartition(self, N: int, dislikes: List[List[int]]) -> bool:
        edge = [[] for _ in range(N + 1)]
        for u, v in dislikes:
            edge[u].append(v)
            edge[v].append(u)
        color = [0] * (N + 1)
        for i in range(1, N + 1):
            if color[i] == 0:
                q = [i]
                color[i] = 1
                while q:
                    cur = q.pop()
                    cur_c = color[cur]
                    for node in edge[cur]:
                        if color[node] == 0:
                            color[node] = cur_c * -1
                            q.append(node)
                        elif color[node] == cur_c:
                            return False
        return True
```
