# 278.
## 题目
You are a product manager and currently leading a team to develop a new product.   
Unfortunately, the latest version of your product fails the quality check.  
Since each version is developed based on the previous version, all the versions after a bad version are also bad.  
Suppose you have `n` versions `[1, 2, ..., n] `and you want to find out the first bad one, which causes all the following ones to be bad.  
You are given an API bool isBadVersion(version) which will return whether version is bad.   
Implement a function to find the first bad version. You should minimize the number of calls to the API.  
## 思路
这道题给定好了一个函数isBadVersion可以判断版本，给定了1到n个版本可以判断版本的正确与否，要求找出第一个错误的版本。  
比较省时的方法大概是二分法，因为数据由1-n已经排好了序，符合二分查找的要求。每次都可以砍掉一半的可能性，比较快。    
写完顺手找了一下别的办法，除了这种非递归的方法，还可以用递归实现。   
## 代码
```ruby
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

class Solution {
public:
    	int firstBadVersion(int n) {
	      int res = -1;
        int low = 1;
        int high = n;
        while (low <= high)
        {
            int mid = low + (high - low) / 2;
            if (isBadVersion(mid))
            {
                res = mid;
                high = mid - 1;
            }
            else
            {
                low = mid + 1;
            }
        }
        return res;
}
};
```
## 递归
```
int recurbinary(int *a, int key, int low, int high)
{
    int mid;
    if(low > high)
        return -1;
    mid = (low + high)/2;
    if(a[mid] == key) return mid;
    else if(a[mid] > key)
        return recurbinary(a,key,low,mid -1);
    else
        return recurbinary(a,key,mid + 1,high);
}
```
