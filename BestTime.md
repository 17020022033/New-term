# 121. 买卖股票的最佳时机
### 题目 
假设你有一个数组，其中第 i 个元素是一支给定股票第 i 天的价格。

如果您只能完成最多一笔交易（即买入和卖出一股股票），则设计一个算法来找到最大的利润。

示例 1:

输入: [7, 1, 5, 3, 6, 4]
输出: 5

最大利润 = 6-1 = 5（不是 7-1 = 6, 因为卖出价格需要大于买入价格）
 

示例 2:

输入: [7, 6, 4, 3, 1]
输出: 0

在这种情况下, 没有交易完成, 即最大利润为 0。
### 分析
这个题用了两种方法。  
当时想到的办法是一个比较暴力的馊主意，设置一个特别大的数组，用来装给的价格里面相减的数。  
如果减出来的数是负的，那就把它放到新设置的数组里，最后再看看哪个数最小，就把它取相反数返回。  
比较糟糕的是因为LeetCode有的样例输入比较大，所以这个数组设置成了1000000这么大。  
运行的时候很担心会超时，幸运的是没有。  
然后想了另外一个办法，不用数组放减出来的结果，在程序运行的时候直接比较。
感觉稍微好一点了。
### 第一次的代码
```ruby
int maxProfit(int* prices, int pricesSize) {
    int total[1000000]={0};
    int x=0;
    int y=0;
    for(int j=0;j<pricesSize;j++)
    for(int i=0;i<j;i++)
    {
    if(prices[i]-prices[j]<0)
    {
    total[x]=prices[i]-prices[j];
        x++;
    }
    }
    for(int i=0;i<x;i++)
        {
        if(y>total[i])
            y=total[i];
        }
    return -y;
}
```
### 第二次的代码
```ruby
int maxProfit(int* prices, int pricesSize) {
    int total = 0;  
        int a = prices[0];  
        for(int i = 0; i < pricesSize; i++)
        {  
            if(prices[i] < a)
                a = prices[i];  
            else
            { 
                int y = prices[i] - a;  
                if(y > total) 
                    total =y;   
            }  
        }  
        return total;  
}
```
