# 题目描述
输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。

## 别人的思路
关键在于如何比较两个数字。将数字转换成字符串s1，s2
通过字符串比较 s1+s2 和 s2+s1 就说明s1 和 s2的顺序。
根据这个比较对原始数据排序，然后组合成新数据。
```
# -*- coding:utf-8 -*-
class Solution:
    def PrintMinNumber(self, numbers):
        # write code here
        strings = []
        for i in numbers:
            strings.append(str(i))
            
        strings.sort(lambda x,y:cmp(x+y,y+x))
        temp = ''.join(strings)

        return temp
```