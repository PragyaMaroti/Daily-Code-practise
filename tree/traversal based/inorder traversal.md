[Problem](https://leetcode.com/problems/increasing-order-search-tree)
### Idea: 
inorder traversal has to be done, when an element is accessed, only the current node's val is to be accessed and processed, to avoid errors(segmentation).
### Implementation:

```cpp
class Solution {
public:
TreeNode * head =NULL;
TreeNode* res = NULL;
TreeNode* increasingBST(TreeNode* root)
{
  if(root==NULL) return NULL // the base case
  increasingBST(root->left) // inorder traversal starts
  if(res==NULL )
  {
    res = new TreeNode(root->val);
    head= res;
  }
  else{
    // not the first element
    res->right =new TreeNode(root->val);
    res= res->right;
  }
  inccreasingBST(root->right)
    return head;
}
};
```
### Results: 
![image](https://user-images.githubusercontent.com/64036955/156969171-697adec4-59b5-4152-b47c-863b6a05a938.png)

