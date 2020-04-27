---
layout:     post
title:      LeetCode 560 Subarray Sum Equals K (Python)
number:     560
level:      Medium
lcurl:      subarray-sum-equals-k
youtube:    Ktd9PT2xgTI
bilibili1:  //player.bilibili.com/player.html?aid=882869912&bvid=BV1vK4y1k7ku&cid=181778664&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

### 解题思路



### 代码
```python
from collections import defaultdict
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        dic = defaultdict(int)
        s = 0
        dic[0] = 1
        res = 0
        for n in nums:
            s += n
            if s - k in dic:
                res += dic[s - k]
            dic[s] += 1
        return res
```