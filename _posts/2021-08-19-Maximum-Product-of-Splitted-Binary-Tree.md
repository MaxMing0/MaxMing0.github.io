---
layout:     post
title:      LeetCode 1339 Maximum Product of Splitted Binary Tree (Python)
number:     1339
level:      Medium
lcurl:      maximum-product-of-splitted-binary-tree
youtube:    ONP1KWm9edI
bilibili1:  //player.bilibili.com/player.html?aid=207457013&bvid=BV1Ch411i7yS&cid=392814007&page=1
xigua:      
date:       2021-08-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given the root of a binary tree, split the binary tree into two subtrees by removing one edge such that the product of the sums of the subtrees is maximized.

Return the maximum product of the sums of the two subtrees. Since the answer may be too large, return it modulo 109 + 7.

Note that you need to maximize the answer before taking the mod and not after taking it.

### 解题思路

先求出整个树的和`s`，再使用dfs遍历整个树，求出每个子树的和`t`，用`t*(s-t)`更新结果

### 代码
```python
class Solution:
    def maxProduct(self, root: Optional[TreeNode]) -> int:
        def dfs(root):
            if not root:
                return 0
            left, right = dfs(root.left), dfs(root.right)
            res[0] = max(res[0], left * (s[0] - left), right * (s[0] - right))
            return left + right + root.val
        
        s = 0
        q = [root]
        while q:
            cur = q.pop()
            s += cur.val
            if cur.left:
                q.append(cur.left)
            if cur.right:
                q.append(cur.right)
        s = [s]
        res = [0]
        dfs(root)
        return res[0] % (10**9 + 7)
```
