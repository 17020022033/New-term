# 203. 删除链表中的元素
## 题目
Remove all elements from a linked list of integers that have value val.
##### Example
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5
##### Credits:
Special thanks to @mithmatt for adding this problem and creating all test cases.
## 思路
## 代码
```ruby
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        if(head==NULL)
            return NULL;
        while(head->val==val||head==NULL){
            head=head->next;
            if(head==NULL)
                return NULL;
        }
        ListNode *temp=head;
        while(temp->next!=NULL)
        {
            if(temp->next->val==val)
                temp->next=temp->next->next;
            else temp=temp->next;
        }
        return head;
    }
};
```
