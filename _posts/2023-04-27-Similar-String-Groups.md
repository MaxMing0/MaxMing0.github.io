---
layout:     post
title:      LeetCode 839 Similar String Groups (Python)
number:     839
level:      Hard
lcurl:      similar-string-groups
youtube:    ukczCqjG408
bilibili1:  
xigua:      
date:       2023-04-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
---

### 题目

Two strings X and Y are similar if we can swap two letters (in different positions) of X, so that it equals Y. Also two strings X and Y are similar if they are equal.

For example, "tars" and "rats" are similar (swapping at positions 0 and 2), and "rats" and "arts" are similar, but "star" is not similar to "tars", "rats", or "arts".

Together, these form two connected groups by similarity: {"tars", "rats", "arts"} and {"star"}.  Notice that "tars" and "arts" are in the same group even though they are not similar.  Formally, each group is such that a word is in the group if and only if it is similar to at least one other word in the group.

We are given a list strs of strings where every string in strs is an anagram of every other string in strs. How many groups are there?

### 解题思路

并查集，初始答案为n，遍历所有组合，如果两个字符串的parent不同，结果减1，并且将他们进行合并

### 代码
```python
class Solution:
    def numSimilarGroups(self, strs: List[str]) -> int:
        def find(v):
            if parent[v] != v:
                parent[v] = find(parent[v])
            return parent[v]

        def union(p1, p2):
            if p1 not in rank:
                rank[p1] = 0
            if p2 not in rank:
                rank[p2] = 0
            if p1 != p2:
                if rank[p1] > rank[p2]:
                    parent[p2] = p1
                else:
                    parent[p1] = p2
                    if rank[p1] == rank[p2]:
                        rank[p2] += 1
        
        def check_similar(s1, s2):
            ret = sum([x != y for x, y in zip(s1, s2)]) in (0, 2)
            return ret
        
        res = n = len(strs)
        rank = {}
        parent = {i: i for i in range(n)}
        for i in range(n - 1):
            for j in range(i + 1, n):
                if check_similar(strs[i], strs[j]):
                    pi, pj = find(i), find(j)
                    if pi != pj:
                        res -= 1
                        union(pi, pj)
        return res
```
