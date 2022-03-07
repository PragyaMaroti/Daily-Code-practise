[Problem](https://leetcode.com/problems/binary-tree-inorder-traversal/)
         
### Implementation:
```cpp
        
class Solution {
public:
    vector<int> ans;
    vector<int> inorderTraversal(TreeNode* root) {
        if(root ==NULL)
        {
            return ans;
            
        }
        inorderTraversal(root->left);
        ans.push_back(root->val);
        inorderTraversal(root->right);
        return ans;
        
        
    }
};
```
          
Results: 
Success Details: 
Runtime: 0 ms, faster than 100.00% of C++ online submissions for Binary Tree Inorder Traversal.
Memory Usage: 10.2 MB, less than 8.77% of C++ online submissions for Binary Tree Inorder Traversal.          
          
          
