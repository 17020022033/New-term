# 412. Fizz Buzz
## 题目
写一个程序，输出从 1 到 n 数字的字符串表示。
1. 如果 n 是3的倍数，输出“Fizz”；
2. 如果 n 是5的倍数，输出“Buzz”；
3.如果 n 同时是3和5的倍数，输出 “FizzBuzz”。
示例：
n = 15,
返回:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
## 思路
用vector定义个长度可变数组，然后判断是不是3和5的余数。  
如果是3或5的余数，按照题目要求输出相应的值。   
如果不是，就需要把整型转化为string类型输出，这也是这道题的点所在。
to_string可以把整型转化为string。  
此外，还可以有以下类型的用法：
```
tring to_string (int val);
string to_string (long val);
string to_string (long long val);
string to_string (unsigned val);
string to_string (unsigned long val);
string to_string (unsigned long long val);
string to_string (float val);
string to_string (double val);
string to_string (long double val);
```
## 代码
```ruby
class Solution {
public:
    vector<string> fizzBuzz(int n) {
        vector<string> a;
        for (int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                a.push_back("FizzBuzz");
            } else if (i % 3 == 0) {
                a.push_back("Fizz");
            } else if (i % 5 == 0) {
                a.push_back("Buzz");
            } else {
                a.push_back(to_string(i));
            }
        }
        return a;
    }
};
```
