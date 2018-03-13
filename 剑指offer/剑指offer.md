# Python语法注意

1. if判断不需要括号，用：替代
2. None是一种不同于数字的类型，不是0，一般用来替代写C时的NULL
   可以给变量赋值None，判断变量是不是None用 
   if var_name is None   和  if var_name is not None
3. 实际上python程序内的变量都是指针，一般情况下对变量操作都是作用在变量指向的那个数据（数据类型任意）。is比较指针内容，==比较指针指向的数据
4. 面向对象编程中，类的方法如果是个递归，则在函数内部调用自己时是 self.function_name
5. 布尔运算的结果是布尔值True或者False,布尔运算有 not and or
6. 正则表达式是一种特殊的字符串，需要配合匹配函数使用。
表达式本身用一些特殊符号表示特殊功能。
同时这些特殊符号可能因为转义字符的原因，在编程语言中被规则改变了形式，从而导致其无法实现自己的特殊功能。
python 提供re 模块使得 r‘字符串’ 这样形式的内容，直接按照正则表达式解读，不需要提前按照字符串规则翻译一遍。
7.python 整除 用 // 得到商 mod得到余数


# 算法技巧点
0.之前运算结果的复用
1. n & (n-1)相当于把n最右边的1变成0
0x80000000 在补码中表示 -2147483648
2.位运算+循环
3.双列表 指针切换，平衡长度差
辅助数据结构
4.逻辑运算符 && 的短路特性
5.快速幂，俗称快速模乘
6.二分法
7.通过栈实现 树的深度优先
8.快慢双指针 
9.joseph ring
10. 树的前中后序遍历非递归实现
```
while stack or p:
    while p:
        #先序在这里visited
        stack.push(p)
        p = p.left
        
''' 树的前中序遍历
    p = stack.pop()
    #中序在这里visited
    p = p.right
'''
'''树的后序遍历
    p = stack.pop()
    if not p.right or lastvisited == p.right:
        #后序在这里visited
        lastvisited = p
    else:
        stack.push(p)
        p = p.right
'''
```
11. 双指针框定范围
12. 树的深度优先（前中后序）遍历的递归，非递归；广度优先的非递归（无递归）