# 477. Total Hamming Distance
## 题目
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.  
Now your job is to find the total Hamming distance between all pairs of the given numbers.  
##### Example:
Input: 4, 14, 2
Output: 6
Explanation: In binary representation, the 4 is 0100, 14 is 1110, and 2 is 0010   
(justshowing the four bits relevant in this case).   
So the answer will be:  
HammingDistance(4, 14) + HammingDistance(4, 2) + HammingDistance(14, 2) = 2 + 2 + 2 = 6.  
##### Note:  
Elements of the given array are in the range of 0 to 10^9  
Length of the array will not exceed 10^4.  
## 思路
做了一简单的汉明距离之后，leetcode给了我这道相似的题目。   
它和汉明距离的不同之处在于要求的是数组内各元素间的汉明距离。  
如果继续用很简单很容易想到的‘^’和‘&’去运算，就很容易出现虽然答案是对的，但是超时的结果。  
所以要用另外一种办法，统计所有数字的同一个位数1出现的次数count，这个位使总的汉明距离增加了count*(n-count).
这…大大降低了所花时间。
## 统计位出现1的次数
```ruby
public class Solution {
    public int totalHammingDistance(int[] nums) {
        int total = 0, n = nums.length;
        for (int j=0;j<32;j++) {
            int bitCount = 0;
            for (int i=0;i<n;i++) 
                bitCount += (nums[i] >> j) & 1;
            total += bitCount*(n - bitCount);
        }
        return total;
    }
}
```
## 用位运算符解
```ruby
class Solution {
public:
    int hammingDistance(int x, int y) {
        int a=0;
        int b=x^y;
        while(b!=0)
        {
            if(b&1!=0)
                a++;
        b=b>>1;
    }
        return a;
    }
};
 ```
