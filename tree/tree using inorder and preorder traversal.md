[Problem Link](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

### Problem Statement:  

Given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the binary tree.    


``` 
Example 1:  

  Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
  Output: [3,9,20,null,null,15,7] 
  
Example 2:
  Input: preorder = [-1], inorder = [-1]
  Output: [-1]


```

### Simple First approach:  

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
    int pointer =0;
    int N ;
    
    //TreeNode* ans;
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        N = preorder.size();
        if(N==1) {
            TreeNode* ans = new TreeNode(preorder[pointer]);
            return ans;
        }
        if(inorder.size()==0)return NULL;
         int n = inorder.size(); // no. of elements this time
        
        TreeNode* ans = new TreeNode(preorder[pointer]);
        
        
        int index = find(inorder.begin(), inorder.end(), preorder[pointer])-inorder.begin();
        
        
        pointer++; // moving to next in preoder element
       
        vector<int> left_side;
        for(int i=0; i<index; i++)
            left_side.push_back(inorder[i]);
        
        vector<int> right_side;
        for(int i=index+1; i<n; i++)
            right_side.push_back(inorder[i]);
        
        if(left_side.size()!=0) ans->left = buildTree(preorder, left_side);
        else ans->left=NULL;
        if(right_side.size()!=NULL) ans->right = buildTree(preorder, right_side);
        else ans->right = NULL;
        
        
        return ans;
       
    }
};   


```

- Result:  

![image](https://user-images.githubusercontent.com/64036955/184469652-829fa988-5b8e-441a-9a2c-f4aacb08ff7b.png)    





