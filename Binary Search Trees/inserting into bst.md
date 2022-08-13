[Problem Statement](https://leetcode.com/problems/insert-into-a-binary-search-tree)

### Problem Statement: 
You are given the root node of a binary search tree (BST) and a value to insert into the tree. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.

Notice that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.    


### Solution:  

```cpp

class Solution {
public: 
    TreeNode* insertIntoBST(TreeNode* root, int target) {

        if(root==NULL)
            root = new TreeNode(target);
        else{
            if(target<root->val)
                root->left=insertIntoBST(root->left, target);
            else
            root->right= insertIntoBST(root->right, target);
        }
        return root;
    }
};

```
- Result:  

![image](https://user-images.githubusercontent.com/64036955/184472996-13a0a7b0-4ea6-473c-970c-eb3e63932293.png)


