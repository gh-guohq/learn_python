# 题目描述
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组,求出这个数组中的逆序对的总数P。并将P对1000000007取模的结果输出。 即输出P%1000000007
## 输入描述:
```
题目保证输入的数组中没有的相同的数字
数据范围：
	对于%50的数据,size<=10^4
	对于%75的数据,size<=10^5
	对于%100的数据,size<=2*10^5
```
## 示例1
输入
```
1,2,3,4,5,6,7,0
```
输出
```
7
```

## 思路
```

```
## 思路

## 最佳思路
归并排序的同时，计数
```
class Solution {
public:
    int InversePairs(vector<int> data) {
         
        int len = data.size();
        if (len<=1)
            return 0;
        vector<int> copy;
        for(int x = 0; x<len; x++)
        {
            copy.push_back(data[x]);
        }
        return fuc(data, copy, 0, len-1);
    }
     
    int fuc(vector<int> &data, vector<int> &copy, int start, int end){ //
         
        if(start == end)
            return 0;
        int mid = (start+end)/2;
        int left = fuc(data, copy, start, mid) % 1000000007;
        int right = fuc(data, copy, mid+1, end) % 1000000007;
       // vector<int> temp;
        long count = 0;
        int i = mid,j = end;
        int index = end;
        while (i >= start && j > mid)
        {
            if (data[i] > data[j])
            {
                //temp.push_back(data[i]);
                copy[index] = data[i];
                index--;
                i--;
                count = count + j - mid;
            }
            else
            {
                //temp.push_back(data[j]);
                copy[index] = data[j];
                index--;
                j--;
            }
        }
        while(i >= start)
        {
            //temp.push_back(data[i]);
            copy[index] = data[i];
            index--;
            i--;
        }
             
        while(j > mid)
        {
            //temp.push_back(data[j]);
            copy[index] = data[j];
            index--;
            j--;
        }
        
        for(int x = start; x <= end; x++)
        {
            data[x] = copy[x];
            //temp.pop_back();
        }

        return (left+right+count)%1000000007;
    }
};
```