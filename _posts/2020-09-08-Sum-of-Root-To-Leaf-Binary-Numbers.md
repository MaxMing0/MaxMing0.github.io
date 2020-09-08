---
layout:     post
title:      LeetCode 1022 Sum of Root To Leaf Binary Numbers (Python)
number:     1022
level:      Easy
lcurl:      sum-of-root-to-leaf-binary-numbers
youtube:    ryabtxIUIHY
bilibili1:  //player.bilibili.com/player.html?aid=329561400&bvid=BV11A411E7AN&cid=233398509&page=1
xigua:      
date:       2020-09-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a binary tree, each node has value 0 or 1.  Each root-to-leaf path represents a binary number starting with the most significant bit.  For example, if the path is 0 -> 1 -> 1 -> 0 -> 1, then this could represent 01101 in binary, which is 13.

For all leaves in the tree, consider the numbers represented by the path from the root to that leaf.

Return the sum of these numbers.

### 解题思路

使用DFS遍历整棵树，遍历时记录从根到当前结点所构成的数，如果是叶节点，则加到结果里

### 代码
```python
class Solution:
    def sumRootToLeaf(self, root: TreeNode) -> int:
        res = 0
        stack = [(root, 0)]
        while stack:
            root, num = stack.pop()
            if root:
                num = (num << 1) | root.val
                if not root.left and not root.right:
                    res += num
                else:
                    stack.append((root.right, num))
                    stack.append((root.left, num))
        return res
```
