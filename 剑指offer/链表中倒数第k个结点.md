# 题目描述
输入一个链表，输出该链表中倒数第k个结点。

## 思路
双指针定位，然后一起移动
```
class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        if not head or k<1:
            return None
        
        tail = head
        for i in range(1,k):
            tail = tail.next
            if not tail:
                return None
                
        while tail.next:
            tail = tail.next
            head = head.next
            
        return head
```