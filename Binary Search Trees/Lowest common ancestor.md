[Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree)

### Problem statement:  

Given a **binary search tree (BST)**, find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself)."   


- Constraints:

1. The number of nodes in the tree is in the range [2, 105].
1. -109 <= Node.val <= 109
1. All Node.val are unique.
1. p != q
1. p and q will exist in the BST.

### Solution:  

```cpp
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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) { 
        int low, high;
        if(p->val < q->val)
        {
            low = p->val;
            high = q->val;
        }
        else{
            low = q->val;
            high = p->val;
        }
        
        if(root->val ==low || root->val ==high)
        {
            return root; // as 1 of them is found, the other must exsist in the subtrees
        }
        if(root->val<high && root->val >low) return root;
        if(root->val>high)
        {
            return lowestCommonAncestor(root->left, p, q);
            
        }
        if(root->val<low)
        {
                        return lowestCommonAncestor(root->right, p, q);

        }
                return NULL;            
    }
};
```

- Results:   
![image](https://user-images.githubusercontent.com/64036955/175770075-a6254861-81cb-4300-826e-e2239cb9bf02.png)


### Optimization 1:  
💡 *Using a different function for comparisons with root value, so as to avoid repetitive comparisons for low and high assignment*   

```cpp
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
    TreeNode* lowestCommonAncestor_helper(TreeNode* root, int low, int high)
    {
         if(root->val ==low || root->val ==high)
        {
            return root; // as 1 of them is found, the other must exsist in the subtrees
        }
        if(root->val<high && root->val >low) return root;
        if(root->val>high)
        {
            return lowestCommonAncestor_helper(root->left, low, high);
            
        }
        if(root->val<low)
        {
                        return lowestCommonAncestor_helper(root->right, low, high);

        }
        return NULL;      
    }
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) { 
        int low, high;
        if(p->val < q->val)
        {
            low = p->val;
            high = q->val;
        }
        else{
            low = q->val;
            high = p->val;
        }
        
       return lowestCommonAncestor_helper(root, low, high);
                      
    }
};
```
-Results:  

![image](https://user-images.githubusercontent.com/64036955/175770234-4312eada-f621-4ff1-8027-368077b95fad.png)






