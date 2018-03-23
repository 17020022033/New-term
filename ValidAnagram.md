# 242. Valid Anagram
## 题目
Given two strings s and t, write a function to determine if t is an anagram of s.  

For example,  
s = "anagram", t = "nagaram", return true.  
s = "rat", t = "car", return false.  
Note:  
You may assume the string contains only lowercase alphabets.  
## 思路
这个题目有一个比较巧妙的解法，可以用数组存字母出现的个数。  
如果两个字符串里字母出现的个数对应相等，就可以说是字符串异位了。  
## 代码
```ruby
class Solution {
public:
	bool isAnagram(string s, string t) {
		int count[256] = { 0 };
		for (int i = 0; i<s.size(); i++) {
			count[s[i]]++;
			count[t[i]]--;
		}
		for (int j = 0; j<26; j++) {
			if (count[j]!=0)
				return false;
		}
		return true;
	}
};
```
