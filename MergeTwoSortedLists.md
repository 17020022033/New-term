# 21.Merge Two Sorted Lists
## 题目
合并两个已排序的链表，并将其作为一个新列表返回。新列表应该通过拼接前两个列表的节点来完成。   
##### 示例：
```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```
## 思路
新建两个结构体变量，一个用来保存头部，一个用来拼接节点。  
如果不新建一个头指针的话，还需要判断一下是从l1开始还是l2开始，感觉会麻烦一点。  
比较需要注意的是拼接完之后要把头指针delete掉。  
## 代码实现
```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
   ListNode *mergeTwoLists(ListNode *l1, ListNode *l2)  
    {  
       ListNode *a=new ListNode(-1);
       ListNode *b=a;
       while(l1!=NULL&&l2!=NULL)
       {
           if(l1->val<=l2->val)
           {
               b->next=l1;
               l1=l1->next;
           }
           else
           {
               b->next=l2;
               l2=l2->next;
           }
           b=b->next;
       }
      if(l1!=NULL)
       {
           b->next=l1;
           l1=l1->next;
       }
      if(l2!=NULL)
       {
           b->next=l2;
           l2=l2->next;
       }
       b=a;
       a=b->next;
       delete (b);
       return a;
    }  
};
```
