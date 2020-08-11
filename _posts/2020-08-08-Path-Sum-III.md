---
layout:     post
title:      LeetCode 437 Path Sum III (Python)
number:     437
level:      Medium
lcurl:      path-sum-iii
youtube:    iMlF6mBMp5g
bilibili1:  //player.bilibili.com/player.html?aid=371637172&bvid=BV1tZ4y1M7JR&cid=223067414&page=1
xigua:      
date:       2020-08-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

### 解题思路

DFS，同时记录路径和出现的次数，每到一个新的点的时候，如果从根开始的的路径和减去目标值存在，答案就加这么多条路径，递归结束要进行回溯

### 代码
```python
class Solution:
    def pathSum(self, root: TreeNode, val: int) -> int:
        def dfs(root, val, cur, dic):
            if not root: 
                return
            cur += root.val
            pre = cur - val
            self.res += dic.get(pre, 0)
            dic[cur] = dic.get(cur, 0) + 1
            dfs(root.left, val, cur, dic)
            dfs(root.right, val, cur, dic)
            dic[cur] -= 1 

        self.res = 0
        dic = {0: 1}
        dfs(root, val, 0, dic)
        return self.res
```
