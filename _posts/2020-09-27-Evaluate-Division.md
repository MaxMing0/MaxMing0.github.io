---
layout:     post
title:      LeetCode 399 Evaluate Division (Python)
number:     399
level:      Medium
lcurl:      evaluate-division
youtube:    EniFQ7XnLnw
bilibili1:  //player.bilibili.com/player.html?aid=372175928&bvid=BV1rZ4y1N7CW&cid=239569011&page=1
xigua:      
date:       2020-09-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

You are given equations in the format A / B = k, where A and B are variables represented as strings, and k is a real number (floating-point number). Given some queries, return the answers. If the answer does not exist, return -1.0.

The input is always valid. You may assume that evaluating the queries will result in no division by zero and there is no contradiction.

### 解题思路

建图，然后做预处理，把所有在一个连通分量里的数，都转换到和某一个特定的数的关系，这样对于每个query，先判断是否出现在一个连通分量里，如果是则直接求出结果，如果都不同时出现在任何一个连通分量中，返回-1

### 代码
```python
class Solution:
    def calcEquation(self, equations: List[List[str]], values: List[float], queries: List[List[str]]) -> List[float]:
        edge = defaultdict(list)
        for i in range(len(equations)):
            x, y = equations[i]
            v = values[i]
            edge[x].append((y, v))
            edge[y].append((x, 1.0 / v))
        clusters = []
        visit = set()
        for x, y in equations:
            dic = {}
            if x not in visit:
                start = x
                visit.add(start)
                dic[start] = 1
                q = [start]
                while q:
                    cur = q.pop()
                    for n, v in edge[cur]:
                        if n not in visit:
                            visit.add(n)
                            q.append(n)
                            dic[n] = dic[cur] * v
            clusters.append(dic)
        res = []
        for x, y in queries:
            for cluster in clusters:
                if x in cluster and y in cluster:
                    res.append(cluster[y] / cluster[x])
                    break
            else:
                res.append(-1)
        return res
```
