# 104.二叉树的最大深度
## 题目
给定一个二叉树，找出其最大深度。  
二叉树的深度为根节点到最远叶节点的最长路径上的节点数。  
案例：  
给出二叉树 [3,9,20,null,null,15,7]，  

    3
   / \
  9  20
    /  \
   15   7
返回最大深度为 3 。  
## 思路
可以用递归去做。每次比较一下左边和右边最大深度再加1.   
二叉树好像经常可以用递归和栈 暂时还在看代码…  
## 代码
```ruby
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
     if(root==NULL)
         return 0;
        int left=maxDepth(root->left);
        int right=maxDepth(root->right);
        return max(left,right)+1;
    }
};
```
