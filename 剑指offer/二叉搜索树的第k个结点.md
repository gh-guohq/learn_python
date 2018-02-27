# 题目描述
给定一颗二叉搜索树，请找出其中的第k大的结点。例如， 5 / \ 3 7 /\ /\ 2 4 6 8 中，按结点数值大小顺序第三个结点的值为4。

##　思路
树的非递归中序遍历，遍历时计数

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回对应节点TreeNode
    def KthNode(self, pRoot, k):
        # write code here
        stack = []
        node = pRoot
        i = 0
        while stack or node:
            while node:
                stack.append(node)
                node = node.left
            
            node = stack.pop()
            i += 1
            if i == k:
                return node
            node = node.right
        
        return None
```

## 思路2
递归中序遍历
```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回对应节点TreeNode
    count = 0
    def KthNode(self, pRoot, k):
        # write code here
        if not pRoot:
            return None
        leftnode = self.KthNode(pRoot.left, k)
        if leftnode:
            return leftnode
        self.count += 1
        if self.count == k:
            return pRoot
        return self.KthNode(pRoot.right, k)
```