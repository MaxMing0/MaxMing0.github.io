---
layout:     post
title:      LeetCode 971 Flip Binary Tree To Match Preorder Traversal (Python)
number:     971
level:      Medium
lcurl:      flip-binary-tree-to-match-preorder-traversal
youtube:    PZ7lLuZRqsU
bilibili1:  //player.bilibili.com/player.html?aid=587290080&bvid=BV1NB4y1P7qL&cid=317220709&page=1
xigua:      
date:       2021-03-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given the root of a binary tree with n nodes, where each node is uniquely assigned a value from 1 to n. You are also given a sequence of n values voyage, which is the desired pre-order traversal of the binary tree.

Any node in the binary tree can be flipped by swapping its left and right subtrees. For example, flipping node 1 will have the following effect:

Flip the smallest number of nodes so that the pre-order traversal of the tree matches voyage.

Return a list of the values of all flipped nodes. You may return the answer in any order. If it is impossible to flip the nodes in the tree to make the pre-order traversal match voyage, return the list [-1].

### 解题思路

递归，如果当前节点的数值与前序遍历不同，则返回-1，如果相同判断左子树和下一个数是否相等，不等则交换当前节点

### 代码
```python
class Solution:
    def flipMatchVoyage(self, root: TreeNode, voyage: List[int]) -> List[int]:
        def dfs (root):
            if not root or self.cur == len(voyage):
                return
            if voyage[self.cur] != root.val:
                self.res = [-1]
                return
            self.cur += 1
            if root.left and root.left.val != voyage[self.cur]:
                self.res.append(root.val)
                dfs(root.right)
                dfs(root.left)
            else:
                if root.left:
                    dfs(root.left)
                if root.right:
                    dfs(root.right)
            
        self.cur = 0
        self.res = []
        dfs(root)
        if self.res and self.res[0] == -1:
            return [-1]
        return self.res
```
