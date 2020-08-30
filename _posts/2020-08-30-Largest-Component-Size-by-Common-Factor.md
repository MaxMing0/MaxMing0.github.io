---
layout:     post
title:      LeetCode 952 Largest Component Size by Common Factor (Python)
number:     952
level:      Hard
lcurl:      largest-component-size-by-common-factor
youtube:    ueAxrFib6Ms
bilibili1:  //player.bilibili.com/player.html?aid=884495694&bvid=BV1oK4y1h7Jt&cid=230570883&page=1
xigua:      
date:       2020-08-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Union Find
    - Math
---

### 题目

Given a non-empty array of unique positive integers A, consider the following graph:

- There are A.length nodes, labelled A[0] to A[A.length - 1];
- There is an edge between A[i] and A[j] if and only if A[i] and A[j] share a common factor greater than 1.
Return the size of the largest connected component in the graph.

### 解题思路

对每个数进行质因数分解，之后使用并查集求连通分量，每次union这个数和它的所有质因子

### 代码
```python
class Solution:
    def largestComponentSize(self, A: List[int]) -> int:
        def find(v):
            if parent[v] != v:
                parent[v] = find(parent[v])
            return parent[v]

        def union(v1, v2):
            p1 = find(v1)
            p2 = find(v2)
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
                        
        def sieve(n):
            primes = [True] * (n + 1)
            p = 2
            while p * p <= n:
                if primes[p]:
                    for i in range(p * 2, n + 1, p):
                        primes[i] = False
                p += 1
            return [element for element in range(2, n) if primes[element]]

        rank = {}
        primes = sieve(max(A) // 2 + 1)
        parent = {i: i for i in A + primes}
        for num in A:
            up = int(sqrt(num))
            t = num
            for p in primes:
                if p > up:
                    break
                if num % p == 0:
                    union(num, p)
                while t % p == 0:
                    t //= p
            if t > 1:
                union(num, t)

        return max(Counter([find(n) for n in A]).values())
```
