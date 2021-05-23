---
layout:     post
title:      LeetCode 968 Binary Tree Cameras (Python)
number:     968
level:      Hard
lcurl:      binary-tree-cameras
youtube:    gxieJ6qdyTI
bilibili1:  //player.bilibili.com/player.html?aid=460700284&bvid=BV1Q5411u72B&cid=342955287&page=1
xigua:      
date:       2021-05-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given the root of a binary tree. We install cameras on the tree nodes where each camera at a node can monitor its parent, itself, and its immediate children.

Return the minimum number of cameras needed to monitor all nodes of the tree.

### 解题思路

贪心维护一个set，存放所有被覆盖的节点，从叶节点向上放，两种情况需要放相机，该节点的左右子树没有相机，或者自己没被覆盖并且是根节点

### 代码
```python
class Solution:
    def minCameraCover(self, root: TreeNode) -> int:
        def dfs(node, par = None):
            if node:
                dfs(node.left, node)
                dfs(node.right, node)

                if (par is None and node not in covered or
                        node.left not in covered or node.right not in covered):
                    self.res += 1
                    covered.update({node, par, node.left, node.right})

        self.res = 0
        covered = {None}
        dfs(root)
        return self.res
```
