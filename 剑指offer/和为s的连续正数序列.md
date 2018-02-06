# 笨办法，枚举，解方程

# 算法 
双指针框定范围，和大于s，则低端指针增加；小于s，则高端指针增加
```
# -*- coding:utf-8 -*-
class Solution:
    def FindContinuousSequence(self, tsum):
        # write code here
        
        a = []
        sum_of_a = 0
        ans = []
        for i in range(1,tsum):
            a.append(i)
            sum_of_a += i
            
            while sum_of_a >= tsum:
                if sum_of_a == tsum:
                    temp = [i for i in a]
                    ans.append(temp)
                    
                sum_of_a -= a.pop(0)
                
        return ans
```