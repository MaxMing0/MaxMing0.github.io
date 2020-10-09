---
layout:     post
title:      LeetCode 449 Serialize and Deserialize BST (Python)
number:     449
level:      Medium
lcurl:      serialize-and-deserialize-bst
youtube:    RSo8v5Xi4CM
bilibili1:  //player.bilibili.com/player.html?aid=797453192&bvid=BV1Ty4y1r7FT&cid=243907629&page=1
xigua:      
date:       2020-10-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
    - Design
---

### 题目

Serialization is converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary search tree. There is no restriction on how your serialization/deserialization algorithm should work. You need to ensure that a binary search tree can be serialized to a string, and this string can be deserialized to the original tree structure.

**The encoded string should be as compact as possible.**

### 解题思路

1. 不考虑BST，直接对树进行前序遍历，空的位置也需要存入，为序列化的结果，反序列化的时候进行递归，如果遇到空返回
2. 考虑BST的性质，序列化的时候不存入空的位置，在反序列化的时候，存入树的范围，如果当前节点在范围内，则为该子树的节点，向下递归，否则返回

### 代码
```python
class Codec:

    def serialize(self, root: TreeNode) -> str:
        """Encodes a tree to a single string.
        """
        if not root:
            return '^'
        return str(root.val) + ' ' + self.serialize(root.left) + ' ' + self.serialize(root.right)

    def deserialize(self, data: str) -> TreeNode:
        """Decodes your encoded data to tree.
        """
        data = deque(data.split(' '))
        def build(data):
            v = data.popleft()
            if v == '^':  
                return None
            node = TreeNode(int(v))
            node.left = build(data)
            node.right = build(data)
            return node
        return build(data)
```
```python
class Codec:

    def serialize(self, root: TreeNode) -> str:
        """Encodes a tree to a single string.
        """
        ret = []
        def preorder(root):
            if root:
                ret.append(root.val)
                preorder(root.left)
                preorder(root.right)
        preorder(root)
        return ' '.join(map(str, ret))

    def deserialize(self, data: str) -> TreeNode:
        """Decodes your encoded data to tree.
        """
        nums = deque(int(n) for n in data.split())
        def build(mmin, mmax):
            if nums and mmin < nums[0] < mmax:
                n = nums.popleft()
                node = TreeNode(n)
                node.left = build(mmin, n)
                node.right = build(n, mmax)
                return node
            
        return build(float('-inf'), float('inf'))
```
