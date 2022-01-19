---
layout:     post
title:      LeetCode 1475 Final Prices With a Special Discount in a Shop (Python)
number:     1475
level:      Easy
lcurl:      final-prices-with-a-special-discount-in-a-shop
youtube:    RCEWhdXqrMM
bilibili1:  
xigua:      
date:       2022-01-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given the array prices where prices[i] is the price of the ith item in a shop. There is a special discount for items in the shop, if you buy the ith item, then you will receive a discount equivalent to prices[j] where j is the minimum index such that j > i and prices[j] <= prices[i], otherwise, you will not receive any discount at all.

Return an array where the ith element is the final price you will pay for the ith item of the shop considering the special discount.

### 解题思路

把每个价格加入栈中，如果当前价格比栈顶元素小，则对栈顶元素进行打折

### 代码
```python
class Solution:
    def finalPrices(self, prices: List[int]) -> List[int]:
        s = []
        for i, p in enumerate(prices):
            while s and prices[s[-1]] >= p:
                prices[s.pop()] -= p
            s.append(i)
        return prices
```
