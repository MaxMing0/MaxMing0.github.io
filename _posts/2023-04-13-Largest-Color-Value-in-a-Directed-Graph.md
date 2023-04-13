---
layout:     post
title:      LeetCode 1857 Largest Color Value in a Directed Graph (Python)
number:     1857
level:      Hard
lcurl:      largest-color-value-in-a-directed-graph
youtube:    r4dqUX5ZyIM
bilibili1:  
xigua:      
date:       2023-04-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Topological Sort
---

### 题目

There is a directed graph of n colored nodes and m edges. The nodes are numbered from 0 to n - 1.

You are given a string colors where colors[i] is a lowercase English letter representing the color of the ith node in this graph (0-indexed). You are also given a 2D array edges where edges[j] = [aj, bj] indicates that there is a directed edge from node aj to node bj.

A valid path in the graph is a sequence of nodes x1 -> x2 -> x3 -> ... -> xk such that there is a directed edge from xi to xi+1 for every 1 <= i < k. The color value of the path is the number of nodes that are colored the most frequently occurring color along that path.

Return the largest color value of any valid path in the given graph, or -1 if the graph contains a cycle.

### 解题思路

对图进行拓扑排序，按照拓扑排序的顺序进行遍历，遍历完如果有环，返回-1，同时维护一个字典，表示以当前节点为结束的路径，每个颜色出现的次数

### 代码
```python
class Solution:
    def largestPathValue(self, colors: str, edges: List[List[int]]) -> int:
        ct = defaultdict(lambda: defaultdict(int))
        graph = defaultdict(list)
        indegree = defaultdict(int)
        for x, y in edges:
            graph[x].append(y)
            indegree[y] += 1
        q = []
        for i in range(len(colors)):
            if i not in indegree:
                q.append(i)
        visited = res = 0
        while q:
            cur = q.pop()
            visited += 1
            ct[cur][colors[cur]] += 1
            res = max(res, ct[cur][colors[cur]])            
            for nei in graph[cur]:
                for c, cnt in ct[cur].items():
                    ct[nei][c] = max(ct[nei][c], cnt)
                indegree[nei] -= 1
                if indegree[nei] == 0:
                    q.append(nei)
        return res if visited == len(colors) else -1
```
