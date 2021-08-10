---
layout:     post
title:      LeetCode 1632 Rank Transform of a Matrix (Python)
number:     1632
level:      Hard
lcurl:      rank-transform-of-a-matrix
youtube:    -HPYs21cPTo
bilibili1:  //player.bilibili.com/player.html?aid=717159370&bvid=BV1KX4y1F7UA&cid=386137277&page=1
xigua:      
date:       2021-08-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
---

### 题目

Given an m x n matrix, return a new matrix answer where answer[row][col] is the rank of matrix[row][col].

The rank is an integer that represents how large an element is compared to other elements. It is calculated using the following rules:

- The rank is an integer starting from 1.
- If two elements p and q are in the same row or column, then:
  - If p < q then rank(p) < rank(q)
  - If p == q then rank(p) == rank(q)
  - If p > q then rank(p) > rank(q)
- The rank should be as small as possible.
It is guaranteed that answer is unique under the given rules.

### 解题思路

将所有数存在字典里，key为数，val为所在位置，将所有数排序，从小到大开始更新rank，当前元素的rank为其所在行列的最大rank+1，同样的数，用并查集维护所在行和列

### 代码
```python
class Solution:
    def matrixRankTransform(self, matrix: List[List[int]]) -> List[List[int]]:
        def find(i):
            if p[i] != i:
                p[i] = find(p[i])
            return p[i]

        n, m = len(matrix), len(matrix[0])
        rank = [0] * (m + n)
        dic = defaultdict(list)
        for i in range(n):
            for j in range(m):
                dic[matrix[i][j]].append([i, j])

        for a in sorted(dic):
            p = list(range(m + n))
            rank2 = rank[:]
            for i, j in dic[a]:
                i, j = find(i), find(j + n)
                p[i] = j
                rank2[j] = max(rank2[i], rank2[j])
            for i, j in dic[a]:
                rank[i] = rank[j + n] = matrix[i][j] = rank2[find(i)] + 1
        return matrix
```
