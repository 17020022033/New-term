# 763. 划分字母区间
## 题目
字符串 S 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一个字母只会出现在其中的一个片段。           
返回一个表示每个字符串片段的长度的列表。           
示例 1:          
输入: S = "ababcbacadefegdehijhklij"         
输出: [9,7,8]       
解释:      
划分结果为 "ababcbaca", "defegde", "hijhklij"。       
每个字母最多出现在一个片段中。         
像 "ababcbacadefegde", "hijhklij" 的划分是错误的，因为划分的片段数较少。        
注意:      
S的长度在[1, 500]之间。      
S只包含小写字母'a'到'z'。      
## 思路
这道题的大方向是用贪心算法解决。       
先用一个数组储存每个出现的字母在字符串里面最后一个位置，然后处理本职情况。         
定两个位置，一前一后地遍历字符串。      
left用来放片段开始的地方，right用来观察当前位置可不可以结束。          
right先把它设置为最右边的和left相同的元素。
然后再找right和left之间有没有相同的然后比当前right更右的元素。遍历一下。有的话就把right移过去。    
如果没有的话，right就是当前片段结束的位置。       
如果可以结束，就用tmp放left和right之间的距离，然后把它放进result里面。      
然后移动片段开始的地方。最后返回result就行了。         
find_last_of可以直接定位到字符串里最后一个该元素。         
## 代码
```ruby
class Solution {
public:
    vector<int> partitionLabels(string S) {
        int left, right;
        int start = 0;
        int end = S.size();
        int tmp = 0;
        int box[26]={0};
        vector<int> result;
        for (int i = 0; i < 26; i++)
            box[i] = S.find_last_of((char)( i + 'a'));
        while (start < end)
        {
            left = start;
            right = box[S[left] - 'a'];
            for (int i = left+1; i <= right; i++)
            {
                if (box[S[i]-'a'] > right) 
                    right = box[S[i] - 'a'];
            }
            tmp=right - left+1;
            result.push_back(tmp);
            start += tmp;
        }
        return result;
    }
};
```
