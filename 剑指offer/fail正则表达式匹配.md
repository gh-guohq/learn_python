# 题目描述
请实现一个函数用来匹配包括'.'和'*'的正则表达式。模式中的字符'.'表示任意一个字符，而'*'表示它前面的字符可以出现任意次（包含0次）。 在本题中，匹配是指字符串的所有字符匹配整个模式。例如，字符串"aaa"与模式"a.a"和"ab*ac*a"匹配，但是与"aa.a"和"ab*a"均不匹配

## fail

## 思路
处理*：
模式第二个字符是*，尝试匹配0个，1个，多个字符三种情况，递归匹配剩下的字符串即可。
将匹配1个归类到多个里面。

```
# -*- coding:utf-8 -*-
class Solution:
    # s, pattern都是字符串
    def match(self, s, pattern):
        # write code here
        i = len(s)
        j = len(pattern)
        if i==0 and j==0:
            return True
        elif i==0 :
            if j==2 and pattern[1] == '*':
                return True
            return False
        elif j==0:
            return False
        
        if j>1 and pattern[1] == '*':
            
            if self.match(s, pattern[2:]):  # ‘*’不起作用
                return True
            if pattern[0] == '.' or pattern[0] == s[0] :
                return self.match(s[1:], pattern)
            return False
                    
            return False
        elif pattern[0] == '.':
            return self.match(s[1:], pattern[1:])
        elif pattern[0] == s[0]:
            return self.match(s[1:], pattern[1:])
        else:
            return False
```

