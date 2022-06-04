-[Link](https://leetcode.com/problems/binary-tree-preorder-traversal/)



Code: 

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
    vector<int> preorderTraversal(TreeNode* root) {
       // vector<int> preorderTraversal(TreeNode* root) {
    if(!root)
        return {};
    vector<int>ans;
    stack<TreeNode*>st;
    st.push(root);
    while(!st.empty()){
        TreeNode* curr = st.top();
        st.pop();
        ans.push_back(curr->val);
        if(curr->right)
            st.push(curr->right);
        
        if(curr->left)
            st.push(curr->left);
    }
    return ans;
}
        
   
};
```
Result:
![image](https://user-images.githubusercontent.com/64036955/171995308-bbf3bc45-8054-4a5b-8a2a-f080b425fcbf.png)
