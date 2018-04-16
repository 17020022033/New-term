# 457. 环形数组循环
## 题目
给定一组含有正整数和负整数的数组。如果某个索引中的 n 是正数的，则向前移动 n 个索引。        
相反，如果是负数(-n)，则向后移动 n 个索引。      
假设数组首尾相接。判断数组中是否有环。环中至少包含 2 个元素。环中的元素一律“向前”或者一律“向后”。          
示例 1：给定数组 [2, -1, 1, 2, 2], 有一个循环，从索引 0 -> 2 -> 3 -> 0。          
示例 2：给定数组[-1, 2], 没有循环。           
注意：给定数组保证不包含元素"0"。         
你能写出时间复杂度为 O(n) 且空间复杂度为 O(1) 的算法吗？       
## 思路
遍历数组，看看有没有那个起点能找到一个环，找到就return。        
具体实现方法是定义两个指针，慢指针初始化为当前位置，快指针跳到下一个索引的位置。      
用一个while循环，如果快指针在的数组元素和起点乘起来不能大于0，就是往后走呗，就肯定不能有环了，去下一个起点。        
如果没有这种情况，那肯定得有环就继续找呗。        
用一个循环调用getNextIndex，如果能够找到两个指针在同一个位置的情况，就算是找到环了。         
## 代码
```ruby
class Solution 
{
public:
     int getNextIndex(int i, vector<int>& a)
    {
        if (i + a[i] > 0)
            return (i + a[i]) % a.size();
        else
            return ((i + a[i]) % a.size() + a.size());
    }

    bool circularArrayLoop(vector<int>& a) 
    {
        for (int i = 0; i < a.size(); i++)
        {
            if (a[i] == 0)
                continue;
            int slow = i;
            int fast = getNextIndex(i, a);
            while (a[i] * a[fast] > 0 && a[i] * a[getNextIndex(fast, a)] > 0)
            {
                if (slow == fast)
                {
                    if (slow == getNextIndex(slow, a))
                        break;
                    else
                        return true;
                }
                else
                {
                    slow = getNextIndex(slow, a);
                    fast = getNextIndex(getNextIndex(fast, a), a);
                }
            }
        }
        return false;
    }
};
```
