# 274. H指数
## 题目
给定一位研究者的论文被引用次数的数组（被引用次数是非负整数）。               
写一个方法计算出研究者的H指数。               
H-index定义: “一位科学家有指数 h 是指他（她）的 N 篇论文中至多有 h 篇论文，分别被引用了至少 h 次，               
其余的 N - h 篇论文每篇被引用次数不多于 h 次。"               
例如，给定 citations = [3, 0, 6, 1, 5]，意味着研究者总共有 5 篇论文，每篇论文相应的被引用了 3, 0, 6, 1, 5 次。               
由于研究者有 3 篇论文每篇至少被引用了 3 次，其余两篇论文每篇被引用不多于 3 次，所以他的h指数是 3 。               
注意： 如果 h 有几个可能的值， h 指数是指其中最大的那个。               
## 思路
这道题需要返回最大的h指数，就直接遍历一下从最大的h指数可能开始排除。         
先把数组排序，用N保存它的大小，N也是H指数可能的最大值。       
从大到小遍历一次H指数的所有可能，如果可以保证当前的H指数可能值符合，那就直接break循环返回它。                   
## 代码
```ruby
class Solution {
public:
    int hIndex(vector<int>& citations) {
        sort(citations.begin(),citations.end());
        int N=citations.size();
        int HIndex=0;
        int temp=N;
        for(int i=0;i<N;i++)
        {
            if(temp<=citations[N-temp])
                if(i>=0&&citations[i-1]<=temp)
                {
                    HIndex=temp;
                break;
                }  
            temp--;
        }
        return HIndex;
    }
};
```
