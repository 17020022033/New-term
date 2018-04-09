# 22. 括号生成
## 题目
给出 n 代表生成括号的对数，请你写出一个能够生成所有可能括号组合的函数。
比如，给出 n = 3，则生成结果为：
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
## 思路
这道题是通过递归来实现的。
用3来举例，它是先返回一个((())),然后又回到((这个地方重新去调用函数补全这个括号顺便把补全好的放进result里。      
补全完((开头的括号，再回到(这个地方去补全括号，再放进result。     
写递归的时候遇到了一个有趣的点。      
自定义函数的时候，如果传入的参数是vector<string> &result就可以正确输出，直接传值就不行。    
改成指针参数也不行，当然这是应该的。      
找了一下资料，感觉可能是因为在这道题的递归里面，因为是递归自己，所以要给它加个引用让它可以每次调用自己的时候修改自己。    
不然的话就像       
```
#include<stdio.h>  
void swap (int a,int b)  
{  
   int t=a;  
   a=b;  
   b=t;  
}  
int main(){  
  int a=3,b=4;  
  swap(a,b);  
  printf("%d %d\n", a, b);  
  return 0;  
}  
```
这样只是做了表面功夫，没有实际更改a和b，只是改变了t的值。           
因为传递的参数是一个值而不是一个变量，所以是会修改失败的。         
这个明明以前上课听过但是当时没学懂，时间一长又忘了🤒     
## 代码
```ruby
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        string element="";
        int x=n,y=n;
        Mykeypoint(result,element,x,y);
    return result;
    }
    void Mykeypoint(vector<string> &result,string element,int x,int y)
    {
        if(x==0&&y==0){
            result.push_back(element);
            return;
        }
        if(x!=0)
        {
            Mykeypoint(result,element+"(",x-1,y);
        }
        if(y!=0&&x<y)
        {
            Mykeypoint(result,element+")",x,y-1);
        }
    }
};
```
