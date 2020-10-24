---
layout:     post
title:      LeetCode 948 Bag of Tokens (Python)
number:     948
level:      Medium
lcurl:      bag-of-tokens
youtube:    FjDzUJodXUY
bilibili1:  //player.bilibili.com/player.html?aid=500119160&bvid=BV1MK411P7K6&cid=249043511&page=1
xigua:      
date:       2020-10-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You have an initial power of P, an initial score of 0, and a bag of tokens where tokens[i] is the value of the ith token (0-indexed).

Your goal is to maximize your total score by potentially playing each token in one of two ways:

- If your current power is at least tokens[i], you may play the ith token face up, losing tokens[i] power and gaining 1 score.
- If your current score is at least 1, you may play the ith token face down, gaining tokens[i] power and losing 1 score.
Each token may be played at most once and in any order. You do not have to play all the tokens.

Return the largest possible score you can achieve after playing any number of tokens.

### 解题思路

贪心，先排序，使用两个指针，每次都是用power将最小一个token换成score，当没有power了就用一个score换区最大的power

### 代码
```python
class Solution:
    def bagOfTokensScore(self, tokens: List[int], P: int) -> int:
        tokens.sort()
        res = score = 0
        l, r = 0, len(tokens) - 1
        while l <= r:
            if tokens[l] <= P:
                P -= tokens[l]
                score += 1
                res = max(res, score)
                l += 1
            else:
                if score:
                    score -= 1
                    P += tokens[r]
                    r -= 1
                else:
                    break
        return res
```
