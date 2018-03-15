# 136. 只出现一次的数字
## 题目
给定一个整数数组，除了某个元素外其余元素均出现两次。请找出这个只出现一次的元素。  
##### 备注：  
你的算法应该是一个线性时间复杂度。 你可以不用额外空间来实现它吗？  
## 思路
题目要求的是线性时间复杂度，意思是尽量少用for循环，也不开新数组。
做这个题最好的办法就是用位运算中的异或去解决它。
这样的话把相同的元素变成0，最后返回一个非0的数。
原本的方法是用了三个循环找出那个数，就比较浪费时间。
感受到位运算的奇妙之处。
## 好的方法
```ruby
class Solution {  
public:  
    int singleNumber(vector<int>& nums) {  
        int length = nums.size();  
    int result = 0 ;  
    for (int i=0; i<length; i++)  
    {  
        result ^= nums[i];  
    }  
    return result;  
    }  
}; 
```
## 坏的方法
```ruby
int singleNumber(int* nums, int numsSize) {
        for(int i=0;i<numsSize;i++)
            for(int j=0;j<numsSize;j++)
          if(i!=j&&nums[i]==nums[j])
          {
          nums[i]=-3;
          nums[j]=-3;
          }
        for(int i=0;i<numsSize;i++)
            if(nums[i]!=-3)
                return nums[i];
    return 0;
};
```
