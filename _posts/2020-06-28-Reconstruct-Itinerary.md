---
layout:     post
title:      LeetCode 332 Reconstruct Itinerary (Python)
number:     332
level:      Medium
lcurl:      reconstruct-itinerary
youtube:    6KMuZdnCvnk
bilibili1:  //player.bilibili.com/player.html?aid=668749586&bvid=BV1qa4y1h7Ti&cid=206782843&page=1
xigua:      
date:       2020-06-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a list of airline tickets represented by pairs of departure and arrival airports [from, to], reconstruct the itinerary in order. All of the tickets belong to a man who departs from JFK. Thus, the itinerary must begin with JFK.

Note:

1. If there are multiple valid itineraries, you should return the itinerary that has the smallest lexical order when read as a single string. For example, the itinerary ["JFK", "LGA"] has a smaller lexical order than ["JFK", "LGB"].
2. All airports are represented by three capital letters (IATA code).
3. You may assume all tickets form at least one valid itinerary.
4. One must use all the tickets once and only once.

### 解题思路

从JFK开始做dfs，每次都先找字典序最小的，并把用过的机票删掉，如果走到一个无法再走的机场，就把他加到结果中，最后的行程单为结果的倒序

### 代码
```python
class Solution:
    def findItinerary(self, tickets: List[List[str]]) -> List[str]:
        def dfs(dep):
            arr = paths[dep]
            while arr:
                dfs(arr.pop())
            res.append(dep)

        res = []
        paths = defaultdict(list)
        tickets.sort(key=lambda x: x[1], reverse=True)
        for s, t in tickets:
            paths[s].append(t)
        dfs('JFK')
        return res[::-1]
```
