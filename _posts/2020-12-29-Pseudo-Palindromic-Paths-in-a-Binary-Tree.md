---
layout:     post
title:      LeetCode 1457 Pseudo-Palindromic Paths in a Binary Tree (Python)
number:     1457
level:      Medium
lcurl:      pseudo-palindromic-paths-in-a-binary-tree
youtube:    vtgzY9se2EQ
bilibili1:  //player.bilibili.com/player.html?aid=843279485&bvid=BV1t54y1t7KK&cid=272555516&page=1
xigua:      
date:       2020-12-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Tree
---

### 题目

Given a binary tree where node values are digits from 1 to 9. A path in the binary tree is said to be pseudo-palindromic if at least one permutation of the node values in the path is a palindrome.

Return the number of pseudo-palindromic paths going from the root node to leaf nodes.

### 解题思路

递归，记录从根到叶节点每个数字出现次数的奇偶性，如果最多一个数字出现了奇数次，则可以构成一个伪回文路径

### 代码
```python
class Solution:
    def pseudoPalindromicPaths (self, root: TreeNode) -> int:
        def dfs(node):
            cur[node.val] = not cur[node.val]
            if not(node.left or node.right):
                if cur.count(False) <= 1:
                    res[0] += 1
                    cur[node.val] = not cur[node.val]
                    return
                
            if node.left:
                dfs(node.left)
            if node.right:
                dfs(node.right)
            cur[node.val] = not cur[node.val]
        
        res = [0]
        cur = [True] * 10
        dfs(root)
        return res[0]
```
