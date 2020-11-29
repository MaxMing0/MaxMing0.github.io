---
layout:     post
title:      LeetCode 1306 Jump Game III (Python)
number:     1306
level:      Medium
lcurl:      jump-game-iii
youtube:    q1ThInEJnU0
bilibili1:  //player.bilibili.com/player.html?aid=800389836&bvid=BV13y4y1q7Gi&cid=261012623&page=1
xigua:      
date:       2020-11-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
    - DFS
---

### 题目

Given an array of non-negative integers arr, you are initially positioned at start index of the array. When you are at index i, you can jump to i + arr[i] or i - arr[i], check if you can reach to any index with value 0.

Notice that you can not jump outside of the array at any time.

### 解题思路

从初始位置开始，进行BFS或者DFS，判断是否能到达0的位置

### 代码
```python
class Solution:
    def canReach(self, arr: List[int], start: int) -> bool:
        n = len(arr)
        s = {start}
        q = [start]
        while q:
            cur = q.pop()
            for nei in (cur + arr[cur], cur - arr[cur]):
                if 0 <= nei < n:
                    if arr[nei] == 0:
                        return True
                    if nei not in s:
                        q.append(nei)
                        s.add(nei)
        return False
```
