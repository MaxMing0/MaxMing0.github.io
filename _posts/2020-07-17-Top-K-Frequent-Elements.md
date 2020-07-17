---
layout:     post
title:      LeetCode 347 Top K Frequent Elements (Python)
number:     347
level:      Medium
lcurl:      top-k-frequent-elements
youtube:    -qKFqJhmllQ
bilibili1:  //player.bilibili.com/player.html?aid=753879303&bvid=BV1sk4y1B7vj&cid=213453922&page=1
xigua:      
date:       2020-07-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Heap
---

### 题目

Given a non-empty array of integers, return the k most frequent elements.

### 解题思路

首先将数组转换成一个Counter，然后使用优先队列找到出现次数最多的k个元素

### 代码
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        q = []
        for num, freq in Counter(nums).items():
            if len(q) == k:
                heappushpop(q, (freq, num))
            else:
                heappush(q, (freq, num))
        return [x[1] for x in q]
```
```
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        ct = Counter(nums)
        return heapq.nlargest(k, ct.keys(), key=ct.get) 
```
