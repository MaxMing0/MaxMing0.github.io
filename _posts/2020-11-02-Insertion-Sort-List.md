---
layout:     post
title:      LeetCode 147 Insertion Sort List (Python)
number:     147
level:      Medium
lcurl:      insertion-sort-list
youtube:    9vy5_wS6MFI
bilibili1:  //player.bilibili.com/player.html?aid=842742678&bvid=BV1F54y1k7oU&cid=251911287&page=1
xigua:      
date:       2020-11-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Sort a linked list using insertion sort.

Algorithm of Insertion Sort:

1. Insertion sort iterates, consuming one input element each repetition, and growing a sorted output list.
2. At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there.
3. It repeats until no input elements remain.

### 解题思路

一个小优化，每次插入的时候，先和插入点pre进行比较，如果小于再从头开始遍历，否则从pre.next开始遍历

### 代码
```python
class Solution:
    def insertionSortList(self, head: ListNode) -> ListNode:
        dummy = ListNode(0)
        pre = dummy
        node = head
        while node:
            cur = node
            node = node.next
            if cur.val < pre.val:
                pre = dummy
            while pre.next and cur.val > pre.next.val:
                pre = pre.next
            cur.next = pre.next
            pre.next = cur
            
        return dummy.next
```
