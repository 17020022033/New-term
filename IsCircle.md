# 141.环形链表
## 题目
给定一个链表，判断链表中否有环。  
## 思路
这道题算是环形链表里面比较简单的，只要求判断是不是环形链表。  
这样可以用两个指针试试，一个快的走两步，一个慢的走一步。  
只要里面有环，就迟早会相遇。要是里面没有环，快的那个就会先走到NULL。  
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
    bool hasCycle(ListNode *head) {
        ListNode *fast=head,*slow=head;
        if(head==NULL||head->next==NULL)  
            return false;  
        while(fast!=NULL&&fast->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow)
                return true;
        }
    return false;
    }
};
```
# 142. 环形链表 II
## 题目
给一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。  
## 思路
画个图发现第一次相遇的时候，起点到第一个节点的距离和相遇的地方到第一个节点的距离相等。  
所以当发现有环的时候，让slow指向头指针，再让两个指针每次各走一步，再相遇的时候就是入环的第一个节点。  
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
    ListNode *detectCycle(ListNode *head) {
                ListNode *fast=head,*slow=head;
        if(head==NULL||head->next==NULL)  
            return NULL;  
        while(fast!=NULL&&fast->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow)
                break;
        }
        if(fast==NULL||fast->next==NULL)
            return NULL;
slow=head;
        while(fast!=slow){
            slow=slow->next;
            fast=fast->next;
        }
        return fast;
    }
};
```
