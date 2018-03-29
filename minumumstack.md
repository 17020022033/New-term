# 155. 最小栈
## 题目
设计一个支持 push，pop，top 操作，并能在常量时间内检索最小元素的栈。
push(x) -- 将元素x推入栈中。
pop() -- 删除栈顶的元素。
top() -- 获取栈顶元素。
getMin() -- 检索栈中的最小元素。
示例:
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.getMin();   --> 返回 -2.
## 思路
第一次试栈，和上学期的汉诺塔好相似欸。
这道题用了两个栈，一个用来存新进来的元素，一个用来存最小值。
一开始push函数的if判断里面写的是a.top()<b.top()，后来发现这样子会导致第一个元素进不来就会N/A。
## 代码
```ruby
class MinStack {
public:
    /** initialize your data structure here. */
    stack<int> a,b;
    MinStack() {}
    void push(int x) {
        a.push(x);
        if(b.size()==0||a.top()<=b.top())
            b.push(x);
    }
    
    void pop() {
        if(a.top()==b.top())
            b.pop();
        a.pop();
    }
    
    int top() {
        return a.top();
    }
    
    int getMin() {
        return b.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```
