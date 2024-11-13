---
layout:     post
title:      LeetCode 116 Populating Next Right Pointers in Each Node (Python)
number:     116
level:      Medium
lcurl:      populating-next-right-pointers-in-each-node
youtube:    
bilibili1:  
xigua:      
date:       2024-11-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Medium
---

### 题目

You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:
```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

### 解题思路

按层进行遍历，遍历当前层的时候，连接下一层。记录每层最左边的节点，从这个节点开始向右连接，全部连接完成之后，从最左边的节点左子树开始进行下一层连接

### 代码
```python
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return root
        leftmost = root
        while leftmost.left:
            cur = leftmost
            while cur:
                cur.left.next = cur.right
                if cur.next:
                    cur.right.next = cur.next.left
                cur = cur.next
            leftmost = leftmost.left
        return root
```
