# 53.最大子序和
## 题目
给定一个序列（至少含有 1 个数），从该序列中寻找一个连续的子序列，使得子序列的和最大。
例如，给定序列[-2, 1, -3, 4, -1, 2, 1, -5, 4]，
连续子序列[4, -1, 2, 1] 的和最大，为 6。
## 思路
这个问题可以直接用三个for循环粗暴地解出来，不过会发现超时。
还可以用在线算法，先求出nums的大小，然后判断a是否为1。
如果是1，就直接输出。
然后从0开始，对Now进行累加，如果发现Now比total大，就把它等过去。
如果Now比0还小，就放弃它可能会让total变大的希望，归零。
## 代码
```ruby
class Solution {
public:
	int maxSubArray(vector<int>& nums) {
		int a = nums.size();
		int Now = 0;
		int total = -100;
		if (a == 1)
		{
			total = nums[0]; return total;
		}
		for (int i = 0; i<a; i++)
		{
			Now = Now + nums[i];
			if (Now>total)
				total = Now;
			if (Now<0)
				Now = 0;
		}
		return total;
	}
};
```
