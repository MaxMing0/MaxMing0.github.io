---
layout:     post
title:      LeetCode 445 Add Two Numbers II (Python)
number:     445
level:      Medium
lcurl:      add-two-numbers-ii
youtube:    xbgBmilSnTs
bilibili1:  //player.bilibili.com/player.html?aid=670138169&bvid=BV17a4y1s7BG&cid=253480168&page=1
xigua:      
date:       2020-11-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

### 解题思路

讲两个链表存入栈中，每次pop两个栈顶元素求和，把进位创建到一个新的节点中，最后返回的时候，如果起始节点是0则返回next，1直接返回该节点

### 代码
```python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        s1 = []
        s2 = []
        while l1 is not None:
            s1.append(l1.val)
            l1 = l1.next
        while l2 is not None:
            s2.append(l2.val)
            l2 = l2.next
        tmp = 0
        res = ListNode(0)
        while len(s1) != 0 or len(s2) != 0:
            if len(s1) != 0:
                tmp += s1.pop()
            if len(s2) != 0:
                tmp += s2.pop()
            res.val = tmp % 10
            head = ListNode(tmp // 10)
            head.next = res
            res = head
            tmp //= 10
        return res.next if res.val == 0 else res
```
