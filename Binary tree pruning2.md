- [Problem's Link](https://leetcode.com/problems/binary-tree-pruning/)

## Problem Statement:

Given the root of a binary tree, return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

A subtree of a node node is node plus every node that is a descendant of node.    

   
Constraints:   

The number of nodes in the tree is in the range [1, 200].
Node.val is either 0 or 1.   

## Solution:  

```cpp
class Solution {
public:
    TreeNode* pruneTree(TreeNode* root) {
        
        if(root==NULL)return root;
        if(root->left==NULL && root->right==NULL)
        {
            if(root->val ==0 ) root = NULL;
            return root;
        }
        if(root->val == 1)
        {
            root->left = pruneTree(root->left);
            root->right = pruneTree(root->right);
            return root;
        }
        
        root->left = pruneTree(root->left);
        root->right = pruneTree(root->right);
        if(root->left == NULL && root->right == NULL)
        {
            return NULL;
        }
        
       // int hasOne = false;
        //TreeNode* temp = NULL;
        //for(int i=0; i<; i++)
        //{
        //}
        return root;
    }
};
```



