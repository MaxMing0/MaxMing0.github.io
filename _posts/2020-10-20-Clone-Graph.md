---
layout:     post
title:      LeetCode 133 Clone Graph (Python)
number:     133
level:      Medium
lcurl:      clone-graph
youtube:    kLljlp3PsIE
bilibili1:  //player.bilibili.com/player.html?aid=500055331&bvid=BV12K411A7Zb&cid=247652359&page=1
xigua:      
date:       2020-10-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Graph
---

### 题目

Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a val (int) and a list (List[Node]) of its neighbors.
```
class Node {
    public int val;
    public List<Node> neighbors;
}
``` 

Test case format:

For simplicity sake, each node's value is the same as the node's index (1-indexed). For example, the first node with val = 1, the second node with val = 2, and so on. The graph is represented in the test case using an adjacency list.

Adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with val = 1. You must return the copy of the given node as a reference to the cloned graph.

### 解题思路

可以使用DFS或者BFS，需要标记访问过的点，例如DFS，就是在遍历neighbor的时候进行递归

### 代码
```python
class Solution:
    def __init__(self):
        self.visit = {}
        
    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node:
            return node
        if node in self.visit:
            return self.visit[node]
        res = Node(node.val, [])
        self.visit[node] = res
        if node.neighbors:
            res.neighbors = [self.cloneGraph(n) for n in node.neighbors]
        return res
```
