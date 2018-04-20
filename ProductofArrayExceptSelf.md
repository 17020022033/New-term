# 238. 除自身以外数组的乘积
## 题目
一个长度为 n 的整形数组nums，其中 n > 1，返回一个数组 output ，其中 output[i] 等于nums中除nums[i]以外所有元素的乘积。  
#### 不用除法 且在O(n)内解决这个问题。  
例如，输入 [1,2,3,4]，返回 [24,12,8,6]。  
进阶：  
你可以在常数空间复杂度内解决这个问题吗？（注意：出于空间复杂度分析的目的，输出数组不被视为额外空间。）  
## 思路
这道题就先从左边遍历一次数组，把当前元素左边的值都乘起来放进数组。  
然后再从右边起遍历一次数组，再把当前元素的右边的值都乘起来放进另外一个数组。  
最后返回一个用来存结果的数组，把当前元素左右的值乘起来放进去。  
## 题目
```ruby
class Solution {  
public:  
    vector<int> productExceptSelf(vector<int>& nums) {    
        vector<int> left(nums.size(), 1);  
        for (int i = 1; i < nums.size(); i++)  
        {  
            left[i] = left[i-1] * nums[i-1];  
        }  
        vector<int> right(nums.size(), 1); 
        for (int i = nums.size() -2; i >= 0; i--)  
        {  
            right [i]= right[i+1] * nums[i+1];  
        }  
        vector<int> result(nums.size(), 1); 
        for (int i = 0; i < nums.size(); i++)  
        {  
            result[i] = left[i] * right[i];  
        }  
        return result;  
    }  
};
```
