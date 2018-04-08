# 287. 寻找重复数
## 题目
一个长度为 n + 1 的整形数组，其中的数字都在 1 到 n 之间，包括 1 和 n ，可知至少有一个重复的数字存在。    
假设只有一个数字重复，找出这个重复的数字。      
注意：              
不能更改数组内容（假设数组是只读的）。               
只能使用恒定的额外空间，即要求空间复杂度是 O(1) 。      
时间复杂度小于 O(n2)                           
数组中只有一个数字重复，但它可能不止一次重复出现。        
## 思路
可以用sort函数把数组排序，然后用while循环去寻找那个重复的数。       
找到重复的数就停下来，然后返回它。      
不过这种办法是…不符合题目要求的，虽然可以AC。       
还可以用二分法解决。       
先找到数组中间的数，为（n+1）/2。
通过找比它小的数的个数的多少，确定重复的数在左区间还是右区间。    
循环往复，就能找到那个重复的数。      
## 代码
```ruby
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int result=0;
        int i=0;
        while(nums[i]!=nums[i+1])
        {
            i++;
        }
        result=nums[i];
        return result;
    }
};
```
## 代码
```ruby
class Solution {  
public:  
    int findDuplicate(vector<int>& nums) {   
        int a = nums.size(); 
        int mid，count=0;
        int low = 1;  
        int high = a-1;  
        while(low < high)  
        {           
            count = 0;  
            mid = (high  + low) / 2; 
            for(int i=0;i<a;i++)  
            {  
                if(nums[i]<=mid)  
                    count ++;  
            }  
            if(count > mid)   
                high = mid;  
            else   
                low = mid+1;  
        }  
        return low;  
    }  
}; 
```
