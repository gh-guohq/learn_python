## 笨办法
```
# -*- coding:utf-8 -*-
class Solution:
    def FindNumbersWithSum(self, array, tsum):
        # write code here
        if not array:
            return []
        
        for i in array:
            l = 0
            r = len(array) -1 
            m = (l+r)/2
            while r>=l:
                if array[m] > tsum - i:
                    r = m-1
                elif array[m] < tsum - i:
                    l = m+1
                else:
                    return i,array[m]
                m = (l+r)/2
        
        return []
```

## 更优解 双指针
```
# -*- coding:utf-8 -*-
class Solution:
    def FindNumbersWithSum(self, array, tsum):
        # write code here
        if not array:
            return []
        
        i = 0
        j = len(array)-1
        
        while i<j:
            if array[i] + array[j] < tsum:
                i += 1
            elif array[i] + array[j] > tsum:
                j -= 1
            else:
                return array[i] , array[j]

        return []
```