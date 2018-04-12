# 83. 删除排序链表中的重复元素
## 题目
给定一个排序链表，删除所有重复的元素使得每个元素只留下一个。       

案例：        

给定 1->1->2，返回 1->2         

给定 1->1->2->3->3，返回 1->2->3       
## 思路
这道题和删除链表中的元素很像，主要是先检查一下链表是不是空的。       
检查完就定义一个指针temp去遍历链表，如果下一个值和当前值一样，那就跳过这个节点删掉它。         
⚡️最后再返回头指针，就行了。不可以返回遍历的指针，它还在链表的尾巴待着，返回它会出不来结果的。             
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
    ListNode* deleteDuplicates(ListNode* head) {
         if(head==NULL)  
            return NULL;
        ListNode* temp=head;
        while(temp->next!=NULL)
        {
            if(temp->next->val==temp->val)
                temp->next=temp->next->next;
            else temp=temp->next;
        }
        
        return head;
    }
};
```
