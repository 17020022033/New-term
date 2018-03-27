# 796.Rotate String
## 题目
We are given two strings, A and B.

A shift on A consists of taking string A and moving the leftmost character to the rightmost position. For example, if A = 'abcde', then it will be 'bcdea' after one shift on A. Return True if and only if A can become B after some number of shifts on A.

Example 1:
Input: A = 'abcde', B = 'cdeab'
Output: true

Example 2:
Input: A = 'abcde', B = 'abced'
Output: false
Note:

A and B will have length at most 100.
## 思路
方法一：
先检查长度是不是一样的，不是返回0；
用一个新的string str储存A+A，在str里面寻找有没有和B完全相同的片段。  
如果有，就返回1；如果没有，就返回0.
方法二：
利用substr函数，可以直接一行代码找到。  
只需要一个for循环，好棒的。    
substr是C++语言函数，主要功能是复制子字符串，要求从指定位置开始，并具有指定的长度。  
## 方法一
```ruby
class Solution {
public:
    bool rotateString(string A, string B) {
        int a=A.size();
        if(a!=B.size())
            return 0;
        if(A==B)
            return 1;
        string str=A+A;
        for(int i=0;i<a;i++)
        {
            int j=0;
            if(str[i]=B[0])
         while(j < a)
         {  
                    if(str[i+j] == B[j])  
                        j++; 
                    else break; 
                }  
            if(j == a) 
                return true;
                }   
        return 0;
    }
};
```
## 方法二
```ruby
class Solution {  
public:  
    bool rotateString(string A, string B) {  
        if(A.length() != B.length())  
            return false;  
        else{  
            int len = A.length();  
            for(int i = 0; i < len; i++)  
                if(A.substr(i,len)+A.substr(0,i) == B)  
                    return true;  
            return false;  
        }  
    }  
};  
```
