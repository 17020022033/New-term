# 693.Binary Number with Alternating Bits
## 题目
Given a positive integer, check whether it has alternating bits: namely,  
if two adjacent bits will always have different values.  
Example 1:  
Input: 5  
Output: True  
Explanation:  
The binary representation of 5 is: 101  
Example 2:  
Input: 7  
Output: False  
Explanation:  
The binary representation of 7 is: 111.  
Example 3:  
Input: 11  
Output: False  
Explanation:  
The binary representation of 11 is: 1011.  
Example 4:  
Input: 10  
Output: True  
Explanation:  
The binary representation of 10 is: 1010.  
## 思路
这道题用&1判断是奇数还是偶数，从而得知最右边的那位是0还是1.
然后用>>向右移动，判断n是否比0大。
这道题比较绝望的地方是没有意识到&的优先级并不比!=高，然后一直WA，试到怀疑LeetCode了Emmmmm.
## 代码
```ruby
class Solution {
public:
    bool hasAlternatingBits(int n) {
        int shangyiwei=11;
        while(n>0){
                if(shangyiwei!=(n&1))
                shangyiwei=n&1;
            else return false;
            n=n>>1;
        }
        return true;
    }
};
```
