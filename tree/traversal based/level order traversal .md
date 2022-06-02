- [Link](https://leetcode.com/problems/binary-tree-level-order-traversal)

### Description:
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

 
```
Example 1:
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
Example 2:

Input: root = [1]
Output: [[1]]
Example 3:

Input: root = []
Output: []
 ```

Constraints:   

- The number of nodes in the tree is in the range [0, 2000].
- -1000 <= Node.val <= 1000


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
vector<vector<int>>ans;
queue<TreeNode*> temp;
    public:
    
    void level()
    {
         //if(root==NULL )return;
        
        int n = temp.size();
        //if(n==0)// starting time
        //{
          //  temp.push(root->val);
        //}
        
            vector<int> temp2(n);
            for(int i=0; i<n; i++)
            {
                TreeNode* p = temp.front();
                temp2[i]=(p->val);
                if(p->left!=NULL)temp.push(p->left);
                if(p->right!=NULL)temp.push(p->right);
                temp.pop();
            }
            ans.push_back(temp2);
        
    }
    
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(root==NULL )return ans;
        //we can insert here as well , the first node's value
        temp.push(root);
        
        while(!temp.empty())
            level();
        return ans;      
        
    }
};

```
- Results: 

![image](https://user-images.githubusercontent.com/64036955/171653252-fde43ba8-27a3-423a-b42c-535c7c2803a0.png)


If the no. of nodes are n then worst case time complexity will be O(n).     
Worst case space complexity will be O(maximum no. of leaf nodes).
