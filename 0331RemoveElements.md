# 203. 删除链表中的元素
## 题目
Remove all elements from a linked list of integers that have value val.  
##### Example  
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6  
Return: 1 --> 2 --> 3 --> 4 --> 5  
##### Credits:  
Special thanks to @mithmatt for adding this problem and creating all test cases.  
## 思路
这道题可以先判断链表是不是空的，空的返回NULL  
然后就用一个while循环判断第一个元素需不需要删除，这里有个点是不能用if   
毕竟可能连续好几个元素都要删除，而且有可能全部节点都需要删除，删完就空了，所以还需要判断一下。  
然后就再从头开始找有没有需要删除的，如果有就跳过它，最后返回。
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
