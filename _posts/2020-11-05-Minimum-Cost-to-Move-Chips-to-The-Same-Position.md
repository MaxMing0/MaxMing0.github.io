---
layout:     post
title:      LeetCode 1217 Minimum Cost to Move Chips to The Same Position (Python)
number:     1217
level:      Easy
lcurl:      minimum-cost-to-move-chips-to-the-same-position
youtube:    DFkgqMl6U_I
bilibili1:  //player.bilibili.com/player.html?aid=627715931&bvid=BV1zt4y1e7fK&cid=252813642&page=1
xigua:      
date:       2020-11-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

We have n chips, where the position of the ith chip is position[i].

We need to move all the chips to the same position. In one step, we can change the position of the ith chip from position[i] to:

- position[i] + 2 or position[i] - 2 with cost = 0.
- position[i] + 1 or position[i] - 1 with cost = 1.
Return the minimum cost needed to move all the chips to the same position.

### 解题思路

奇数移动到奇数，偶数移动到偶数花费是0，奇数偶数相互移动花费是1，结果是全移动到奇数，或全移动到偶数，所以结果为，奇数和偶数中少的

### 代码
```python
class Solution:
    def minCostToMoveChips(self, position: List[int]) -> int:
        even = 0
        for c in position:
            if c % 2 == 0:
                even += 1
        return min(even, len(position) - even)
```
