# 283. Move Zeroes
## 题目描述
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.  
For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].  
Note:  
You must do this in-place without making a copy of the array.  
Minimize the total number of operations.  
给出数组，把0移到数组的最末端，不能再用新的数组，用的步骤要尽量少。
## 代码
```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
          int n=0;
        int a=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]!=0)
            {
                nums[a]=nums[i];
                a++;
            }
            else if(nums[i]==0)
                n++;
        }
    for(int i=a;i<nums.size();i++)
    {
        nums[i]=0;
    }
    }
};
```
## 分析
因为不能够再开新的数组，所以就直接用nums.size()直接求出数组内元素的数量，把数组里所有非零的数都移到最左边，然后再把数量正确的零放在数组的最右边。
