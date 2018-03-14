# 27.移除元素
## 题目 
给定一个数组和一个值，在这个数组中原地移除指定值和返回移除后新的数组长度。  
不要为其他数组分配额外空间，你必须使用 O(1) 的额外内存原地修改这个输入数组。  
元素的顺序可以改变。超过返回的新的数组长度以外的数据无论是什么都没关系。  
#### 示例:  
```
给定 nums = [3,2,2,3]，val = 3，  
你的函数应该返回 长度 = 2，数组的前两个元素是 2。  
```
## 代码
```ruby
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int numsSize=nums.size();
        if (numsSize == 0 || numsSize == 1 && val == nums[0])
     return NULL;
        int a=numsSize;
   int j = numsSize - 1;
for (int i = 0; i<numsSize; i++)
{
       if (nums[i]==val)
           a--;
	while (nums[i] == val&&i != j&&numsSize != 0)
	{
		if (nums[j] != val)
		{
			nums[i] = nums[j];
			j--;
		}
		else if (nums[j] == val)
			j--;
	}
}
        return a;
}};
```
## 思路
这道题做的时候我主要存在两个问题。  
因为提交代码的时候看到输出显示的是一个数组，就理所当然的以为是返回数组。  
然而题目写着是原地修改完数组之后输出数组的长度，在这里就WA了很多次。  
第二个问题是算法很绕很长，分类讨论如果输出数组是0就输出NULL。  
如果不是的话就用i从前往后找val，找到了就和最后面的不是val的换一下位置，然后代码就比较繁琐。  
Emmmmmmmmmm，然而别人用三行搞定了这个问题，只需要用i和j从前往后遍历数组就行了。  
以后做完题一定要找找更好的办法，寻找改进的空间。
## 他山之石
```ruby
class Solution {  
public:  
    int removeElement(vector<int>& nums, int val) {  
        int length = nums.size();  
        int j = 0;  
        for(int i = 0; i<length; i++){  
            if(nums[i] != val)  
                nums[j++] = nums[i];  
        }  
        return j;  
          
    }  
};  
```
