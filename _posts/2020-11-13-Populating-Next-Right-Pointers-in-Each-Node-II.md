---
layout:     post
title:      LeetCode 117 Populating Next Right Pointers in Each Node II (Python)
number:     117
level:      Medium
lcurl:      populating-next-right-pointers-in-each-node-ii
youtube:    4wzBM_w0thM
bilibili1:  //player.bilibili.com/player.html?aid=970367031&bvid=BV1np4y1r7fQ&cid=255388988&page=1
xigua:      
date:       2020-11-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - BFS
---

### 题目

Given a binary tree
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

**Follow up:**
- You may only use constant extra space.
- Recursive approach is fine, you may assume implicit stack space does not count as extra space for this problem.

### 解题思路

BFS，遍历每一行的时候，记录下一行的第一个节点，以及记录遍历到的上一个节点，每次遍历到一个新的节点时，用上一个节点指向当前节点

### 代码
```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        cur = root
        head, pre = None, None
        while cur:
            if cur.left:
                if pre:
                    pre.next = cur.left
                else:
                    head = cur.left
                pre = cur.left

            if cur.right:
                if pre:
                    pre.next = cur.right
                else:
                    head = cur.right
                pre = cur.right

            cur = cur.next
            if not cur:
                cur = head
                pre, head = None, None

        return root
```
