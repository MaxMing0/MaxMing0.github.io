---
layout:     post
title:      LeetCode 173 Binary Search Tree Iterator (Python)
number:     173
level:      Medium
lcurl:      binary-search-tree-iterator
youtube:    dG7VOUSItzs
bilibili1:  //player.bilibili.com/player.html?aid=500534267&bvid=BV1qK41137h1&cid=264671898&page=1
xigua:      
date:       2020-12-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
    - Design
---

### 题目

Implement the BSTIterator class that represents an iterator over the in-order traversal of a binary search tree (BST):

- BSTIterator(TreeNode root) Initializes an object of the BSTIterator class. The root of the BST is given as part of the constructor. The pointer should be initialized to a non-existent number smaller than any element in the BST.
- boolean hasNext() Returns true if there exists a number in the traversal to the right of the pointer, otherwise returns false.
- int next() Moves the pointer to the right, then returns the number at the pointer.

Notice that by initializing the pointer to a non-existent smallest number, the first call to next() will return the smallest element in the BST.

You may assume that next() calls will always be valid. That is, there will be at least a next number in the in-order traversal when next() is called.

### 解题思路

可以先在构造函数中把中序遍历求出来，或者使用栈进行遍历

### 代码
```python
class BSTIterator:

    def __init__(self, root: TreeNode):
        self.stack = []
        self.do_left(root)

    def do_left(self, root):
        while root:
            self.stack.append(root)
            root = root.left
            
    def next(self) -> int:
        ret = self.stack.pop()
        if ret.right:
            self.do_left(ret.right)
        return ret.val

    def hasNext(self) -> bool:
        return len(self.stack) > 0
```
