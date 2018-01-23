# Python语法注意

1. if判断不需要括号，用：替代
2. None是一种不同于数字的类型，不是0，一般用来替代写C时的NULL
   可以给变量赋值None，判断变量是不是None用 
   if var_name is None   和  if var_name is not None
3. 实际上python程序内的变量都是指针，一般情况下对变量操作都是作用在变量指向的那个数据（数据类型任意）。is比较指针内容，==比较指针指向的数据
4. 面向对象编程中，类的方法如果是个递归，则在函数内部调用自己时是 self.function_name
5. 布尔运算的结果是布尔值True或者False,布尔运算有 not and or