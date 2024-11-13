---
layout:     post
title:      LeetCode 426 Convert Binary Search Tree to Sorted Doubly Linked List (Python)
number:     426
level:      Medium
lcurl:      convert-binary-search-tree-to-sorted-doubly-linked-list
youtube:    
bilibili1:  
xigua:      
date:       2024-11-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Convert a Binary Search Tree to a sorted Circular Doubly-Linked List in place.

You can think of the left and right pointers as synonymous to the predecessor and successor pointers in a doubly-linked list. For a circular doubly linked list, the predecessor of the first element is the last element, and the successor of the last element is the first element.

We want to do the transformation in place. After the transformation, the left pointer of the tree node should point to its predecessor, and the right pointer should point to its successor. You should return the pointer to the smallest element of the linked list.

### 解题思路

DFS中序遍历，记录最小的节点（第一个节点）和上一个节点，当前节点左指针指向上一个节点，上一个节点的右指针指向当前节点，最后再把第一个和最后一个节点连接起来

### 代码
```python
class Solution:
    first, last = None, None
    def treeToDoublyList(self, root: 'Optional[Node]') -> 'Optional[Node]':
        def dfs(root):
            if not root:
                return
            dfs(root.left)
            if self.last:
                self.last.right = root
                root.left = self.last
            else:
                self.first = root
            self.last = root
            dfs(root.right)

        if not root:
            return None
        dfs(root)
        self.last.right = self.first
        self.first.left = self.last
        return self.first
```
