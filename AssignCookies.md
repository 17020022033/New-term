# 455. Assign Cookies
## 题目
Assume you are an awesome parent and want to give your children some cookies.   
But, you should give each child at most one cookie.   
Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with;   
and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content.   
Your goal is to maximize the number of your content children and output the maximum number.  
#### Note:  
You may assume the greed factor is always positive.   
You cannot assign more than one cookie to one child.  
#### Example 1:
``` 
Input: [1,2,3], [1,1]  
Output: 1  
Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3.   
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.  
You need to output 1.
```  
#### Example 2:
```
Input: [1,2], [1,2,3]
Output: 2
Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```
## 代码
```ruby
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        int a=g.size();
        int b=s.size();
        sort(g.begin(), g.end());
        sort(s.begin(), s.end());
        int total=0;
        for(int i=0,j=0;i<a&&j<b;)
        {
            if(g[i]<=s[j])
            {
                total++;
                i++;
                j++;
            }
            else if(g[i]>s[j])
                j++;
        }
        return total;
    }
};
```
## 思路
题目是有孩子有饼干，每个孩子都有自己的满足值，给的饼干大于等于满足值就会开心。
题目会给两个数组，一个存孩子的满足值，一个存饼干的大小。
这道题用一个sort函数给数组排好序，然后就可以用贪心算法根据数字大小统计一下到底有多少个孩子能吃上饼干。
感觉算法真的是编程的灵魂诶…
