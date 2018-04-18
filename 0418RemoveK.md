# 402. 移掉K位数字
## 题目
给定一个以字符串表示的非负整数 num，移除这个数中的 k 位数字，使得剩下的数字最小。  
注意:  

num 的长度小于 10002 且 ≥ k。  
num 不会包含任何前导零。  
示例 1 :  

输入: num = "1432219", k = 3  
输出: "1219"  
解释: 移除掉三个数字 4, 3, 和 2 形成一个新的最小的数字 1219。  
示例 2 :  

输入: num = "10200", k = 1  
输出: "200"  
解释: 移掉首位的 1 剩下的数字为 200. 注意输出不能有任何前导零。  
示例 3 :  

输入: num = "10", k = 2  
输出: "0"  
解释: 从原数字移除所有的数字，剩余为空就是0。  
## 思路
先定义一个temp用来装结果的子串。  
首先判断一下，是k大还是数组的长度大。如果k大，直接返回0。  
然后如果没有返回，就遍历num。  
如果可删除的数比0大，就进while循环，看看能不能删除temp的上一个元素。  
如果还可以删除，当前元素又比上一个元素小，就不删了。不然就删掉它。  
默认每一个当前元素都会先被放进temp里存一下。    
最后用while循环看看有没有前导0，就返回结果串temp。
## 代码
```ruby
class Solution {
public:
    string removeKdigits(string num, int k) {
        string temp;
        int leftdelete = k;
        int startval = 0;
        if(k >= num.size()) 
        {
            return "0";
        }
        for(int i=0;i<num.size();i++)
        {
            while(leftdelete > 0 )
            {
                if(num[i] >= temp.back())
                    break;
                leftdelete--;
                temp.pop_back();
            }
            temp.push_back(num[i]);
        }
        while(temp[startval]=='0') 
            startval++;
        temp = temp.substr(startval, num.size()-k-startval);
        if(temp.size()==0)
            return "0";
        else return temp;
    }
};
```
