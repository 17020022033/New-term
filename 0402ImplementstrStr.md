# 28. 实现strStr()
## 题目
实现 strStr()。  
返回蕴含在 haystack 中的 needle 的第一个字符的索引，如果 needle 不是 haystack 的一部分则返回 -1 。  
例 1:  
输入: haystack = "hello", needle = "ll"  
输出: 2  
例 2:  
输入: haystack = "aaaaa", needle = "bba"  
输出: -1  
## 思路
首先判断特殊情况是否haystack长度比needle短，如果是，就直接返回无；  
然后用一个for循环遍历一次haystack，嵌套for循环寻找里面有没有相同的字符串。  
如果发现有哪一个对不上，就跳出当前循环继续遍历haystack。  
如果找到了相同的字符串，就返回进入循环的时候的i值。  
如果没有，就直接输出-1.  
## 代码
```ruby
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(haystack.size()<needle.size())
            return -1;
        for (int i = 0; i < haystack.size(); i++) {
            int j = 0;
            for (j = 0; j < needle.size(); j++) {
                if (haystack[i + j] == needle[j]) 
                    continue;
                else break;
            }
            if (j == needle.size()) 
                return i;
        }
        return -1;
    }
};
```
