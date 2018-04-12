# 206. 反转链表
## 题目
反转一个单链表。
## 思路
这个链表反转用了迭代的方法实现。     
先判断链表是不是空的，再判断是不是只有一个元素。      
如果都不是，就设置三个指针开始反转它。       
fast指针初始化为NULL，想的是它跑在最前面，指着链表的下一个元素免得链表断掉。      
middle用头指针初始化，想从它在的地方开始反转。      
slow指针就用来放尾巴，就是已经反转好的部分。         
具体实现的过程中，先让fast指向下一个元素，然后middle指向slow这个之前反转好的部分，然后分别移动slow和middle到下一个位置。      
然后再判断一下符不符合循环的条件。   
如果不符合，就最后让middle再指向新尾巴那串反转好的部分，然后返回掉这串反转好的代码。       
## 代码
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
    ListNode* reverseList(ListNode* head) {
        if(head==NULL)
            return NULL;
        if(head->next==NULL)
            return head;
        ListNode* fast=NULL;
        ListNode* slow=NULL;
        ListNode* middle=head;
        while(middle->next!=NULL)
        {
            fast=middle->next;
            middle->next=slow;
            slow=middle;
            middle=fast;
        }
        middle->next=slow;
        return middle;
    }
};
```
