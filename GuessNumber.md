# 374.猜数游戏
## 题目
我们正在玩猜数游戏。 游戏如下：
我从 1 到 n 选择一个数字。 你需要猜我选择了哪个号码。
每次你猜错了，我会告诉你这个数字是高还是低。
你调用一个预定义的接口 guess(int num)，它会返回 3 个可能的结果（-1，1 或 0）：
```
-1 : 我的数字比较低
 1 : 我的数字比较高
 0 : 恭喜！你猜对了！
 ```
案例:
```
n = 10, 我选择 6.

返回 6.
```
## 分析
这道题给了一个预定义的函数可以用来判断对错，使用二分法循环可以猜出正确数。  
一开始没看懂题目，不明白guess函数怎么用，后来发现其实它就是靠输出-1,0，1告诉你猜测的对错。  
```ruby
if (a == 1)
lower = b;
if (a == -1)
higher = b;
```
然后用上面这段错误代码runtime error，发现它可能会卡进循环里。   
之后调整了一下lower和higher的值，这样如果算完刚好要猜的数是lower或者higher也能再从循环跳出来了。
## 代码
```ruby
// Forward declaration of guess API.
// @param num, your guess
// @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
int guess(int num);

class Solution {
public:
	int guessNumber(int n) {
		int a = 0, b = 0, lower = 1;
		int total = 1;
		int higher = n;
		while (1) {
				b = lower+(higher - lower) / 2;
				a = guess(b);
				if (a == 0)
				{
					total = b;
					break;
				}
				if (a == 1)
					lower = b+1;
				if (a == -1)
					higher = b-1;
			}
		return total;
	}
};
```
