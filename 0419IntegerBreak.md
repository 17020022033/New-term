# 343. 整数拆分
## 题目
给定一个正整数 n，将其拆分为至少两个正整数的和，并使这些整数的乘积最大化。 返回你可以获得的最大乘积。  

例如，给定 n = 2，返回1（2 = 1 + 1）；给定 n = 10，返回36（10 = 3 + 3 + 4）。  

注意：你可以假设 n 不小于2且不大于58。  
## 思路
可以观察到，如果是2或者3或者4，整数的拆分都是没什么规律的。  
但是如果是5以及以上的数，就是除以三的商的n次方再乘上余数。  
然后再返回就成。  
## 代码实现
```ruby
class Solution {
public:
    int integerBreak(int n) {
        if(n==2)
            return 1;
        if(n==3)
            return 2;
        if(n==4)
            return 4;
        int result=1;
        while (n > 4) {
            result *= 3;
            n -= 3;
        }
        result=result*n;
        return result;
    }
};
```
