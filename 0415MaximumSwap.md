# 670. 最大交换
## 题目
给定一个非负整数，你至多可以交换一次数字中的任意两位。返回你能得到的最大值。         
##### 示例 1 :            
输入: 2736               
输出: 7236             
解释: 交换数字2和数字7。             
##### 示例 2 :              
输入: 9973               
输出: 9973                
解释: 不需要交换。            
##### 注意:          
给定数字的范围是 [0, 108]           
## 思路
先定义一个动态数组，然后把这个数的每个数字放进去。因为用的是%10放的，所以要用reverse把它翻转回来。        
然后用一个for循环找当前数组中的最大的数，找到了就试试看能不能和最前面的数交换。          
因为最多只能换一次，所以换完就返回结果。           
## 代码
```ruby
class Solution {
public:
    int maximumSwap(int num) {
        int total = 0;
        vector<int> result;
        int temp = num;
        
        while(temp!=0)
        {
            result.push_back(temp % 10);
            temp= temp/10;
        }
        
        int a=result.size();
        reverse(result.begin(),result.end());
        
        for(int i=0; i<a; i++)
        {
            int max = result[i];
            int keynumber = 0;
            
            for(int j=i; j<a; j++)
            {
                if(result[j] >= max)
                {
                    keynumber = j;
                    max = result[j];
                }
            }
            
            if(max > result[i])
            {
                swap(result[i], result[keynumber]);
                for(int i=0; i<a; i++)
                {
                    total = result[i]+total*10;
                }
                return total;
            }
        }
        return num;
    }
};

```
