---
layout:     post
title:      LeetCode 797 All Paths From Source to Target (Python)
number:     797
level:      Medium
lcurl:      all-paths-from-source-to-target
youtube:    ypQ-D5YvXLk
bilibili1:  //player.bilibili.com/player.html?aid=668991857&bvid=BV1qa4y1E7sg&cid=216078993&page=1
xigua:      
date:       2020-07-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

Given a directed, acyclic graph of N nodes.  Find all possible paths from node 0 to node N-1, and return them in any order.

The graph is given as follows:  the nodes are 0, 1, ..., graph.length - 1.  graph[i] is a list of all nodes j for which the edge (i, j) exists.

### 解题思路

维护一个队列，从0开始进行遍历，每次都将队列的所有路径进行拓展，如果到达n-1就是一个结果

### 代码
```python
class Solution:
    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        n = len(graph)
        res = []
        paths = [[0]]
        while paths:
            tmp = []
            for path in paths:
                if path[-1] == n - 1:
                    res.append(path)
                    continue
                for node in graph[path[-1]]:
                    tmp.append(path + [node])
            paths = tmp
        return res
```
