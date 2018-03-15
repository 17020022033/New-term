# 717.1比特与2比特字符
## 题目
有两种特殊字符。第一种字符可以用一比特0来表示。第二种字符可以用两比特(10 或 11)来表示。  
现给一个由若干比特组成的字符串。问最后一个字符是否必定为一个一比特字符。给定的字符串总是由0结束。  
```
示例 1:
输入: 
bits = [1, 0, 0]
输出: True
解释: 
唯一的编码方式是一个两比特字符和一个一比特字符。所以最后一个字符是一比特字符。
示例 2:
输入: 
bits = [1, 1, 1, 0]
输出: False
解释: 
唯一的编码方式是两比特字符和两比特字符。所以最后一个字符不是一比特字符。
```
注意:
```
1 <= len(bits) <= 1000.
bits[i] 总是0 或 1.
```
## 倒序找
```
bool isOneBitCharacter(int* bits, int bitsSize) {
    {
        int a=0;
        for(int i=bitsSize-2;i>=0;i--)
        {
            if(bits[i]==1)
                a++;
            if(bits[i]==0)
                break;
        }
        if(a%2==0)
            return true;
        else return false;
    }
}
```
## 顺序找
```
bool isOneBitCharacter(int* bits, int bitsSize) {
    {
        int a=0;
        if(bitsSize==1)
            return true;
       for(int i=0;i<bitsSize;i++)
       {
           if(bits[i]==1)
           {i++;
           a=0;}
           else a=1;
       }
        return a;
}}
```
## 思路
如果是倒序找的话，可以从后面看最后一个0前面有多少个连续的1；   
如果是顺序找的话，可以每次遇到1就i加两次，然后令a为0，遇到0就加一次i，令a为1，最后直接返回a。  