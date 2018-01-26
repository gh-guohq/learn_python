# 包含min函数的栈

```
# -*- coding:utf-8 -*-
class Solution:
    def push(self, node):
        # write code here
        self.stack.append(node)
    def pop(self):
        # write code here
        return self.stack.pop()
    def top(self):
        # write code here
        return self.stack[0]
    def min(self):
        # write code here
        min_num = self.stack[0]
        for i in self.stack:
            if i < min_num:
                min_num = i
        return min_num
    
    def __init__(self):
        self.stack = []
```

## 辅助栈思路

```
class Solution:
    def push(self, node):
        # write code here
        self.stack.append(node)
        if not self.minnum:
            self.minnum.append(node)
        elif node < self.minnum[-1]:
            self.minnum.append(node)
        else:
            self.minnum.append(self.minnum[-1])
        
    def pop(self):
        # write code here
        self.minnum.pop()
        return self.stack.pop()
    
    def top(self):
        # write code here
        return self.stack[-1]
    
    def min(self):
        # write code here
        return self.minnum[-1]
    
    def __init__(self):
        self.stack = []
        self.minnum = []
```