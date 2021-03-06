# 378. 有序矩阵中第K小的元素
## 题目
给定一个 n x n 矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。       
请注意，它是排序后的第k小元素，而不是第k个元素。      
示例:      
```
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
```
k = 8,        
返回 13。       
说明:       
你可以假设 k 的值永远是有效的, 1 ≤ k ≤ n2 。       
## 思路
这道题直观的方法是遍历一次放到新容器里，然后排序再直接返回第k个数。     
sort默认是从小到大排序所以compare函数都省了。      
另一种办法是…别人的办法。
因为用的容器没见过，就放了进来。    
如果当前值大于等于堆顶，跳过该行继续遍历。   
否则将数字存入堆中并删除堆顶数字。   
最后返回堆顶。    
vector查找最后一个元素用back。
## 代码实现
```ruby
class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        vector<int> total;
        for(int i=0;i<matrix.size();i++)
            for(int j=0;j<matrix[0].size();j++)
                total.push_back(matrix[i][j]);
        sort(total.begin(),total.end());
        return total[k-1];
    }
};
```
## 代码实现
```ruby
class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        priority_queue<int> heap;
        for(int i=0; i<matrix.size(); ++i) {
            for(int j=0; j<matrix[0].size(); ++j) {
                if(heap.size() < k) heap.push(matrix[i][j]);
                else {
                    if(heap.top() <= matrix[i][j]) break;
                    else {
                        heap.push(matrix[i][j]);
                        heap.pop();
                    }
                }
            }
        }
        return heap.top();
    }
};
```
