---
layout:     post
title:      LeetCode 1443 Minimum Time to Collect All Apples in a Tree (Python)
number:     1443
level:      Medium
lcurl:      minimum-time-to-collect-all-apples-in-a-tree
youtube:    3af7CQoV848
bilibili1:  
xigua:      
date:       2020-05-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Tree
---

### 题目

Given an undirected tree consisting of n vertices numbered from 0 to n-1, which has some apples in their vertices. You spend 1 second to walk over one edge of the tree. Return the minimum time in seconds you have to spend in order to collect all apples in the tree starting at vertex 0 and coming back to this vertex.

The edges of the undirected tree are given in the array edges, where edges[i] = [fromi, toi] means that exists an edge connecting the vertices fromi and toi. Additionally, there is a boolean array hasApple, where hasApple[i] = true means that vertex i has an apple, otherwise, it does not have any apple.

### 解题思路

DFS, 统计为了采到所有苹果，需要走到的边，如果一条边需要走到，就一定要走两次，否则是无法回去的，最后的结果就是 要走到的边数 * 2

DFS返回的结果就是，从这个点开始，要走到的边数，以及这个点需不需要走到，如果后面有苹果或者这个点有苹果，就是需要走到的

### 代码
```python
class Solution:
    def minTime(self, n: int, edges: List[List[int]], hasApple: List[bool]) -> int:
        def dfs(node):
            tmp = 0
            for v in edge[node]:
                t, apple = dfs(v)
                tmp += t + int(apple)
            return tmp, (tmp > 0) or hasApple[node]
        
        edge = defaultdict(list)
        for x, y in edges:
            edge[x].append(y)
        return dfs(0)[0] * 2
```
