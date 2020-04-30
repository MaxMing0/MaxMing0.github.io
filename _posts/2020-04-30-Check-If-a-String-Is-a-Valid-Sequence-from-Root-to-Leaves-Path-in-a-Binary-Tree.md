---
layout:     post
title:      LeetCode Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree (Python)
number:     9999
level:      na
lcurl:      
youtube:    69RASNxY1us
bilibili1:  //player.bilibili.com/player.html?aid=540480955&bvid=BV1Mi4y1b7Yj&cid=185153400&page=1
xigua:      
date:       2020-04-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

Given a binary tree where each path going from the root to any leaf form a valid sequence, check if a given string is a valid sequence in such binary tree. 

We get the given string from the concatenation of an array of integers arr and the concatenation of all values of the nodes along a path results in a sequence in the given binary tree.

### 解题思路

DFS, 递归的时候需要记录当前递归到的节点，以及对应数组中的位置，如果当前节点的数值和对应数组的数值不同返回`False`

如果已经到了数组中的最后一个数，就判断当前节点是否为页节点， 其他情况继续递归节点的左右子树以及对应数组中的下个数

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidSequence(self, root: TreeNode, arr: List[int]) -> bool:
        def dfs(root, pos):
            if not root or root.val != arr[pos]:
                return False
            if pos == len(arr) - 1:
                return not root.left and not root.right
            return dfs(root.left, pos + 1) or dfs(root.right, pos + 1)
        
        return dfs(root, 0)
```
