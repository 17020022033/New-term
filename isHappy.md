# 202.快乐数
## 题目
写一个算法来判断一个数是不是“快乐数”。  
一个数是不是快乐是这么定义的：  
对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，或是无限循环但始终变不到 1。  
如果可以变为 1，那么这个数就是快乐数。  
## 思路
输入一个数，用一个while循环使这个数替换为它每个位置上的数字的平方和。  
再用一个数组，存储这个数每次替换的数。  
每替换出一个新数，就在数组中找一找有没有重复的。  
如果有重复的，就不是快乐数。如果编程了1，就是快乐数。  
## 代码实现
```ruby
	class Solution {
public:
    bool isHappy(int n) {
      	int hash1[256] = { 0 };
		int total=0,i=0;
		if (n < 10 && n!=1)
			n = n*n;
		while (n != 1)
		{
			while (n >=10)
			{
				total = total+(n % 10)*(n % 10);
				n = n / 10;
				if (n < 10)
					total = total + n*n;
			}
			if (total < 10 )
				total = total*total;
			hash1[i] = total;
			n = total;
			if (total == 1)
				return true;
			for (int j = 0; j < i; j++)
			{
				if (total == hash1[j])
					return false;
			}	
			total = 0;
			i++;
		}
		return true;
    }
};
```
