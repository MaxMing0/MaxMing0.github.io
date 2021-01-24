---
layout:     post
title:      LeetCode 23 Merge k Sorted Lists (Python)
number:     23
level:      Hard
lcurl:      merge-k-sorted-lists
youtube:    20QAhrE-jhQ
bilibili1:  //player.bilibili.com/player.html?aid=798759492&bvid=BV1Ty4y1178e&cid=287158040&page=1
xigua:      
date:       2021-01-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Priority Queue
    - Sort
---

### 题目

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

### 解题思路

把每个链表的第一个元素已经链表的标号放到优先队列里，每次pop最小的，如果后面仍有元素就继续加入到队列里

### 代码
```python
class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        q = []
        for i in range(len(lists)):
            if lists[i]:
                heapq.heappush(q, (lists[i].val, i))
                lists[i] = lists[i].next
        res = ListNode()
        cur = res
        while q:
            val, i = heapq.heappop(q)
            cur.next = ListNode(val)
            cur = cur.next
            if lists[i]:
                heapq.heappush(q, (lists[i].val, i))
                lists[i] = lists[i].next
        return res.next
```
