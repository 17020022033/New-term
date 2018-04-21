# 739. 每日温度
## 题目
根据每日 气温 列表，请重新生成一个列表，对应位置的输入是你需要再等待多久温度才会升高的天数。如果之后都不会升高，请输入 0 来代替。  

例如，给定一个列表 temperatures = [73, 74, 75, 71, 69, 72, 76, 73]，你的输出应该是 [1, 1, 4, 2, 1, 1, 0, 0]。  

提示：气温 列表长度的范围是 [1, 30000]。每个气温的值的都是 [30, 100] 范围内的整数。  
## 思路
首先设置两个容器，stack和vector类型的，再定义一个整型变量存下一个升温的天数。  
用for循环从右边开始遍历一次数组，先用while循环检查一下下一个升温日是什么时候。  
如果栈是空的，就下一个升温日是0.如果栈不是空的，就把栈顶的值和当前天数减一减，差就是下一个升温日。  
然后把当前天数放到栈里，再把当前升温日插到数组头部。  
如果某个栈顶比它的前面的温度数字要小，那它就会被删除出去。因为没有是下一个升温日的可能了。以此类推。  
所以关键是找那个没有被删除的栈顶和当前天数的差。  
## 代码实现
```ruby
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        int nextday=0;
        stack<int> temp;
        vector<int> result;
        for (int i=temperatures.size()-1; i>=0; i--)
        {
            while(temp.size()>0 && temperatures[temp.top()] <= temperatures[i])
            {
                temp.pop();
            }
            if(temp.size()==0)
                nextday=0;
            else nextday=temp.top()-i;
            temp.push(i);
            result.insert(result.begin(), nextday);
        }
        return result;
    }
};
```
