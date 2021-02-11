---
layout:     post
title:      LeetCode 138 Copy List with Random Pointer (Python)
number:     138
level:      Medium
lcurl:      copy-list-with-random-pointer
youtube:    G1-jKbessG8
bilibili1:  //player.bilibili.com/player.html?aid=501644596&bvid=BV1BN411R7a8&cid=296205876&page=1
xigua:      
date:       2021-02-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.

Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. None of the pointers in the new list should point to nodes in the original list.

For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> y.

Return the head of the copied linked list.

The linked list is represented in the input/output as a list of n nodes. Each node is represented as a pair of [val, random_index] where:

- val: an integer representing Node.val
- random_index: the index of the node (range from 0 to n-1) that the random pointer points to, or null if it does not point to any node.
Your code will only be given the head of the original linked list.

### 解题思路

递归，使用字典存每个节点的克隆节点，递归next和random指针

### 代码
```python
class Solution:
    def __init__(self):
        self.visit = {None: None}

    def copyRandomList(self, head: 'Node') -> 'Node':
        if head in self.visit:
            return self.visit[head]
        node = Node(head.val, None, None)
        self.visit[head] = node
        node.next = self.copyRandomList(head.next)
        node.random = self.copyRandomList(head.random)
        return node
```
