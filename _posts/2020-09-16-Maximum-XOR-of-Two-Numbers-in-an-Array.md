---
layout:     post
title:      LeetCode 421 Maximum XOR of Two Numbers in an Array (Python)
number:     421
level:      Medium
lcurl:      maximum-xor-of-two-numbers-in-an-array
youtube:    ZHtZfkAcPKc
bilibili1:  //player.bilibili.com/player.html?aid=584568143&bvid=BV1s64y1F7Wm&cid=235885551&page=1
xigua:      
date:       2020-09-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a non-empty array of numbers, a0, a1, a2, … , an-1, where 0 ≤ ai < 231.

Find the maximum result of ai XOR aj, where 0 ≤ i, j < n.

Could you do this in O(n) runtime?

### 解题思路

从最高位开始，先假设该位置可以为1，然后与每个数进行异或，查看结果是否也在输入的数中，如果不在，则该位为0

### 代码
```python
class Solution:
    def findMaximumXOR(self, nums: List[int]) -> int:
        res = 0
        for i in range(31, -1, -1):
            res <<= 1
            pre = {n >> i for n in nums}
            res += any(res ^ 1 ^ p in pre for p in pre)
        return res
```
