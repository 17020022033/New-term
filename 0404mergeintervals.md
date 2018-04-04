# 56.合并区间
## 题目
给出一个区间的集合, 请合并所有重叠的区间。  
示例：  
给出 [1,3],[2,6],[8,10],[15,18],  
返回 [1,6],[8,10],[15,18].  
## 思路
把输入的区间的begin从小到大排序。   
然后定义一个新的vector容器，如果哪个intervals是空的，那就直接返回空的容器。    
如果不是空的，就先把第一个intervals输进去，然后做遍历。分三个条件。    
如果容器里的end比下一个的start要大而且比下一个end要小，就用下一个intervals的end代替现在的。      
如果容器的end只是比下一个start大，那就继续遍历。           
如果容器里的end比下一个的start小，那就当没事发生把下一个intervals放进去好了。          
Emmmmm  用sort给vector排序的时候，MyCompare函数要写具体方法，sort里面直接结构体.begin()和.end()就行了。        
## 代码实现
```ruby
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */
class Solution {
public:
    static bool Mycompare1(const Interval &a, const Interval &b) {
        return a.start < b.start;
    }
    vector<Interval> merge(vector<Interval>& intervals) {
        sort(intervals.begin(), intervals.end(), Mycompare1);
        vector<Interval>total;
        if (intervals.size() == 0) 
        {
            return total;
        }
        total.push_back(intervals[0]);
        for (int i = 1; i < intervals.size(); i++) 
        {
            if (total.back().end >= intervals[i].start&&total.back().end<=intervals[i].end) 
            {
                total.back().end=intervals[i].end;
            }
            if(total.back().end >= intervals[i].start)
            {
                continue;
            }
            else 
            {
                total.push_back(intervals[i]);
            }
        }
        return total;
    }
};
```
