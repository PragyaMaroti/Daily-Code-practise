[Link](https://leetcode.com/problems/validate-binary-search-tree/)


### Problem Statement:  

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
 
 
 - Constraints:

1. The number of nodes in the tree is in the range [1, 104].
1. -2^31 <= Node.val <= 2^31 - 1


### Solution:  

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> ans;
    void helper_function(TreeNode* root)
    {
        if(root==NULL) return;
        //if(root->left == nullptr && root->right ==nullptr) ans.push_back(root->val);
        helper_function(root->left);
        ans.push_back(root->val);
        helper_function(root->right);
    }
    bool isValidBST(TreeNode* root) {
      // doing a pre-order traversal, the vector should be sorted;
        helper_function(root);
        int n = ans.size();
        for(int i=0; i<n-1; i++)
        {   //cout<< ans[i]<<endl;
            if(ans[i]>=ans[i+1])return false;
        }
        return true;
    }
};
```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/175770521-01f1c8ac-37e4-4c61-a0ca-b30457e8f811.png)

🗃️ O(N) , N= no. of nodes.   
⏰ O(N), N = no. of nodes. (O(2N) though)
