---
layout:     post
title:      LeetCode 239 Sliding Window Maximum (Python)
number:     239
level:      Hard
lcurl:      sliding-window-maximum
youtube:    W2zQSExW04s
bilibili1:  //player.bilibili.com/player.html?aid=287949414&bvid=BV1Bf4y1v758&cid=260875513&page=1
xigua:      
date:       2020-11-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sliding Window
---

### 题目

You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

### 解题思路

使用一个双向队列来维护滑动窗口的最大值，保持降序，队首元素为当前最大值，如果超出范围出队

### 代码
```python
from collections import deque
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)
        res = []
        q = deque()
        for i in range(n):
            while q and nums[q[-1]] < nums[i]:
                q.pop()
            q.append(i)
            if q[0] == i - k:
                q.popleft()
            if i >= k - 1:
                res.append(nums[q[0]])
        return res
```
