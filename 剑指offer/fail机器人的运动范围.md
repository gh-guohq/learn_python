# 题目描述
地上有一个m行和n列的方格。一个机器人从坐标0,0的格子开始移动，每一次只能向左，右，上，下四个方向移动一格，但是不能进入行坐标和列坐标的数位之和大于k的格子。 例如，当k为18时，机器人能够进入方格（35,37），因为3+5+3+7 = 18。但是，它不能进入方格（35,38），因为3+5+3+8 = 19。请问该机器人能够达到多少个格子？

## 思路 
没想出来

## 回溯法
使用map标记进入过的块，回溯或者DFS保证完全遍历
递归，非递归方法均可
```
# -*- coding:utf-8 -*-
class Solution:
    def movingCount(self, threshold, rows, cols):
        # write code here
        a = [[0 for i in range(cols)] for j in range(rows)]
        
        def CanIn(x,y):
            temp = 0
            if x<0 or x>=rows or y<0 or y >=cols:
                return False
            if a[x][y] == 1:
                return False
            for i in str(x):
                temp += int(i)
            for j in str(y):
                temp += int(j)
            if temp > threshold:
                a[x][y] = 1
                return False
            else:
                return True
        
        temp = [(0,0)]
        count = 0
        while temp:
            x,y = temp.pop(0)
            if CanIn(x,y):
                a[x][y] = 1
                count += 1
                temp.extend([(x-1,y),(x+1,y),(x,y-1),(x,y+1)])
        
        return count
```