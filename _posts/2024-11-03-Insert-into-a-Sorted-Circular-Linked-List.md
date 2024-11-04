---
layout:     post
title:      LeetCode 708 Insert into a Sorted Circular Linked List (Python)
number:     708
level:      Medium
lcurl:      insert-into-a-sorted-circular-linked-list
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - LinkedList
---

### 题目

Given a Circular Linked List node, which is sorted in non-descending order, write a function to insert a value insertVal into the list such that it remains a sorted circular list. The given node can be a reference to any single node in the list and may not necessarily be the smallest value in the circular list.

If there are multiple suitable places for insertion, you may choose any place to insert the new value. After the insertion, the circular list should remain sorted.

If the list is empty (i.e., the given node is null), you should create a new single circular list and return the reference to that single node. Otherwise, you should return the originally given node.

### 解题思路

如果head为空，直接创建一个新节点

两个指针，前一个节点和当前节点，如果要插入的数在这两个节点之间，在这里插入，如果在链表的起点和终点（前一个节点大于当前节点），如果要插入的数，比最大的大，或者比最小的小，在这里插入

特殊情况，链表里所有的值相同，遍历一圈又回到head了，在直接在这里插入

### 代码
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, next=None):
        self.val = val
        self.next = next
"""

class Solution:
    def insert(self, head: 'Optional[Node]', insertVal: int) -> 'Node':
        if not head:
            node = Node(insertVal, None)
            node.next = node
            return node
        pre, cur = head, head.next
        flag = False
        while True:
            if pre.val <= insertVal <= cur.val:
                flag = True
            elif pre.val > cur.val:
                if pre.val <= insertVal or insertVal <= cur.val:
                    flag = True
            if flag:
                pre.next = Node(insertVal, cur)
                return head
            pre, cur = cur, cur.next
            if pre == head:
                break
        pre.next = Node(insertVal, cur)
        return head
```
