# 495. 提莫攻击
## 题目
在《英雄联盟》的世界中，有一个叫“提莫”的英雄，他的攻击可以让敌方英雄艾希（编者注：寒冰射手）进入中毒状态。                       
现在，给出提莫对艾希的攻击时间序列和提莫攻击的中毒持续时间，你需要输出艾希的中毒状态总时长。                       
你可以认为提莫在给定的时间点进行攻击，并立即使艾希处于中毒状态。                       
示例1:                       
输入: [1,4], 2                       
输出: 4                       
原因: 在第1秒开始时，提莫开始对艾希进行攻击并使其立即中毒。中毒状态会维持2秒钟，直到第2秒钟结束。                       
在第4秒开始时，提莫再次攻击艾希，使得艾希获得另外2秒的中毒时间。                       
所以最终输出4秒。                       
示例2:                       
输入: [1,2], 2                       
输出: 3                       
原因: 在第1秒开始时，提莫开始对艾希进行攻击并使其立即中毒。中毒状态会维持2秒钟，直到第2秒钟结束。                       
但是在第2秒开始时，提莫再次攻击了已经处于中毒状态的艾希。                       
由于中毒状态不可叠加，提莫在第2秒开始时的这次攻击会在第3秒钟结束。                       
所以最终输出3。                       
注意：                       
你可以假定时间序列数组的总长度不超过10000。                       
你可以假定提莫攻击时间序列中的数字和提莫攻击的中毒持续时间都是非负整数，并且不超过10,000,000。                       
## 思路
定义三个变量，总时长，上一个攻击，当前攻击。然后进for循环遍历数组。                      
进数组之后先调整两个攻击的值，为上一个攻击和当前攻击，然后就开始判断加多少时间。                      
如果减起来比中毒时间长，那肯定是直接加进去total里。                      
如果有叠加的时间，就把没叠加的加上去。                        
遍历完成返回total就好。                       
因为是在for循环外面初始化当前攻击和上一个攻击的值，需要timeSeries[0]，所以需要考虑一个数组是空的的情况。                      
## 代码实现
```ruby
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int total=0;
        if(timeSeries.size()==0)
            return total;
        int lastattack=0;
        int nowattack=timeSeries[0];
        for(int i=0;i<timeSeries.size();i++)
        {
            lastattack=nowattack;
            nowattack=timeSeries[i];
            if(nowattack-lastattack>=duration||nowattack==timeSeries[0])
            {
                total=total+duration;
            }
            else if(nowattack-lastattack<duration)
                total=total+(nowattack-lastattack);
        }
        return total;
    }
};
```
