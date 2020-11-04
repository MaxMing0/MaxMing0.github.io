---
layout:     post
title:      LeetCode 310 Minimum Height Trees (Python)
number:     310
level:      Medium
lcurl:      minimum-height-trees
youtube:    AxlhJzKGOec
bilibili1:  //player.bilibili.com/player.html?aid=330222799&bvid=BV1eA411j7XQ&cid=252509480&page=1
xigua:      
date:       2020-11-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
    - Topological Sort
---

### 题目

A tree is an undirected graph in which any two vertices are connected by exactly one path. In other words, any connected graph without simple cycles is a tree.

Given a tree of n nodes labelled from 0 to n - 1, and an array of n - 1 edges where edges[i] = [ai, bi] indicates that there is an undirected edge between the two nodes ai and bi in the tree, you can choose any node of the tree as the root. When you select a node x as the root, the result tree has height h. Among all possible rooted trees, those with minimum height (i.e. min(h))  are called minimum height trees (MHTs).

Return a list of all MHTs' root labels. You can return the answer in any order.

The height of a rooted tree is the number of edges on the longest downward path between the root and a leaf.

### 解题思路

找到这个树最靠中心的点作为根节点，树的高度会最小，这道题可以转化成拓扑排序，每次删除所有度为1的点，直到最后只剩下一个或两个点，为最后的结果

### 代码
```python
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        edge = [set() for _ in range(n)]
        for u, v in edges:
            edge[u].add(v)
            edge[v].add(u)
        q = [x for x in range(n) if len(edge[x]) < 2]
        tmp = []
        while True:
            for node in q:
                for n in edge[node]:
                    edge[n].remove(node)
                    if len(edge[n]) == 1:
                        tmp.append(n)
            if not tmp:
                break
            tmp, q = [], tmp
        return q
```
