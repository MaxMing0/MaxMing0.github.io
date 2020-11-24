---
layout:     post
title:      LeetCode 337 House Robber III (Python)
number:     337
level:      Medium
lcurl:      house-robber-iii
youtube:    Apr_4dQly7U
bilibili1:  //player.bilibili.com/player.html?aid=712917247&bvid=BV1WD4y1X7JQ&cid=259098209&page=1
xigua:      
date:       2020-11-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.

### 解题思路

DP,f(n)表示抢该节点的最优值，g(n)表示不抢这个点的最优值，`max(f(root), g(root))`为所求
```
f[root] = root.val + g[root.left] + g[root.right]
g[root] = max(f[root.left], g[root.left]) + max(f[root.right], g[root.right])
```

### 代码
```python
class Solution:
    def rob(self, root: TreeNode) -> int:
        def dfs(root):
            if not root:
                return
            dfs(root.left)
            dfs(root.right)
            f[root] = root.val + g[root.left] + g[root.right]
            g[root] = max(f[root.left], g[root.left]) + max(f[root.right], g[root.right])
            
        f, g = defaultdict(int), defaultdict(int)
        dfs(root)
        return max(f[root], g[root])
```
```python
class Solution:
    def rob(self, root: TreeNode) -> int:
        def dfs(root):
            if not root:
                return (0, 0)
            left = dfs(root.left)
            right = dfs(root.right)
            f = root.val + left[1] + right[1]
            g = max(left) + max(right)
            return (f, g)
        
        return max(dfs(root))
```
