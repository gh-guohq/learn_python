# 失败

## 逻辑运算符 && 的短路特性
```
class Solution {
public:
    int Sum_Solution(int n) {
        int ans = n;
        ans && (ans += Sum_Solution(n - 1)); //ans = 0 后面不做
        return ans;
    }
};
```

## 将乘法化解为加法

原理就是，类似快速幂，俗称快速模乘。
a * b 可以这样算
```
res = 0
while(a){
    if(a & 1) res += b;
    a >>= 1;
    b <<= 1; 
}
```
原理是把a拆成2的幂的和，a = 2^e0 + 2^e1 + 2^e2....
那么 a * b = (2^e0 + 2^e1 + 2^e2+...) * b = b * 2^e0 + b * 2^e1 + b * 2^e2 + ...= (b << e0) + (b << e1) + ....
在知道数据类型的字节大小的情况下，可以不通过循环，直接执行32（int类型）遍移位加和操作