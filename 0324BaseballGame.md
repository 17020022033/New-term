# 682.Baseball Game
## 题目
You're now a baseball game point recorder.  

Given a list of strings, each string can be one of the 4 following types:  

Integer (one round's score): Directly represents the number of points you get in this round.  
"+" (one round's score): Represents that the points you get in this round are the sum of the last two valid round's points.  
"D" (one round's score): Represents that the points you get in this round are the doubled data of the last valid round's points.  
"C" (an operation, which isn't a round's score): Represents the last valid round's points you get were invalid and should be removed.  
Each round's operation is permanent and could have an impact on the round before and the round after.  

You need to return the sum of the points you could get in all the rounds.  

Example 1:  
Input: ["5","2","C","D","+"]  
Output: 30  
Explanation:   
Round 1: You could get 5 points. The sum is: 5.  
Round 2: You could get 2 points. The sum is: 7.  
Operation 1: The round 2's data was invalid. The sum is: 5.    
Round 3: You could get 10 points (the round 2's data has been removed). The sum is: 15.  
Round 4: You could get 5 + 10 = 15 points. The sum is: 30.  
Example 2:  
Input: ["5","-2","4","C","D","9","+","+"]  
Output: 27  
Explanation:   
Round 1: You could get 5 points. The sum is: 5.  
Round 2: You could get -2 points. The sum is: 3.  
Round 3: You could get 4 points. The sum is: 7.  
Operation 1: The round 3's data is invalid. The sum is: 3.    
Round 4: You could get -4 points (the round 3's data has been removed). The sum is: -1.  
Round 5: You could get 9 points. The sum is: 8.  
Round 6: You could get -4 + 9 = 5 points. The sum is 13.  
Round 7: You could get 9 + 5 = 14 points. The sum is 27.  
Note:  
The size of the input list will be between 1 and 1000.  
Every integer represented in the list will be between -30000 and 30000.  
## 思路
定义一个函数用来获取当前字符的大小，再定义一个数组来储存每轮的值。
最后判断一下当前字符是不是特殊的，跳到不同的条件就ok了。
对我来说比较困难的是自定义的这个获得当前字符值的函数…
## 代码
```ruby
using namespace std;
class Solution {
public:
	int getNum(string& s) {
		int num;
		stringstream s1;
		s1 << s;
		s1 >> num;
		return num;
	}
	int calPoints(vector<string>& ops) {
		int total=0,lun = 1;
        int e[1000]={0};
		for (int i = 0; i < ops.size(); i++)
		{	
			if (ops[i] == "C")
			{
                
				lun--;
                total=total-e[lun];
			}
			else if (ops[i] == "D")
			{
				total = total + 2 * e[lun-1]; 
				e[lun] = 2*e[lun-1];
				lun++;
			}
			else if (ops[i] == "+")
			{
				total = total + e[lun-1] +e[lun-2];
				e[lun] = e[lun - 1] + e[lun - 2];
				lun++;
			}
			else
			{
				total = total + getNum(ops[i]);
                e[lun]= getNum(ops[i]);
				lun++;
		}
		}
		return total;
	}
};
```
