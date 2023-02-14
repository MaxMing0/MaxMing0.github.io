---
layout:     post
title:      LeetCode 904 Fruit Into Baskets (Python)
number:     904
level:      Medium
lcurl:      fruit-into-baskets
youtube:    qp-v5AGTJ5Q
bilibili1:  
xigua:      
date:       2023-02-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Two Pointers
---

### 题目

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

### 解题思路

双指针，维护一个字典作为篮子，key是水果的种类，value是目前篮子里的个数，移动右指针把水果加入到篮子里，如果超过2种水果，移动左指针，并减少对于水果，直到符合要求。每次移动右指针之后更新结果。

### 代码
```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        i = j = res = 0
        basket = {}
        while j < len(fruits):
            if fruits[j] in basket:
                basket[fruits[j]] += 1
            else:
                while len(basket) == 2:
                    basket[fruits[i]] -= 1
                    if basket[fruits[i]] == 0:
                        basket.pop(fruits[i])
                    i += 1
                basket[fruits[j]] = 1
            res = max(res, j - i + 1)
            j += 1
        return res
```
