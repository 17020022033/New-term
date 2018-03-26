# 1. 两数之和
## 题目
给定一个整数数列，找出其中和为特定值的那两个数。
你可以假设每个输入都只会有一种答案，同样的元素不能被重用。
```
示例:
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```
## 思路
这道题主要还是熟悉一下容器的使用还有vector数组嗯。   
办法就是先用for循环存元素，边存边找找有没有办法能够和为target的数字。  
.find可以在容器中，找不到就返回.end()，找到了就返回地址。  
另外一点是，原本我用的是vector<int> result，就一直报错。  
现在明白了是一定要初始化才能使用。（2，0）这种形式2是长度0是初始化值。😞  
## 代码
```ruby
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result(2,0);
      map<int,int> mapnums;
        for(int i=nums.size(); i--; mapnums[nums[i]]=i)
        {
            if (mapnums.find(target-nums[i]) != mapnums.end()) 
            {
            result[0] = i;   
            result[1] = mapnums[target-nums[i]];
            return result;
            }
        }
        return result;
    }
};
```
