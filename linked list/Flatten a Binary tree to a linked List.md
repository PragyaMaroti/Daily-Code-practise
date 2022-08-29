- [Problem's Link](https://practice.geeksforgeeks.org/problems/flatten-binary-tree-to-linked-list/1)
   
### Problem Statement:   


Given a binary tree, flatten it into linked list in-place. Usage of auxiliary data structure is not allowed. After flattening, left of each node should point to NULL and right should contain next node in preorder.   

![image](https://user-images.githubusercontent.com/64036955/187139519-b30bfad7-de9e-47cd-862b-0d426842f8c2.png)    
![image](https://user-images.githubusercontent.com/64036955/187139581-f9eb1112-1ed0-4f91-b2ac-4dbdca042147.png)


Your task is to complete the function flatten() which takes the root of the tree and flattens the tree into a linkes list without using any auxiliary space.    
Note : The driver code prints the inorder traversal of the flattened binary tree.   


### Solution:  


``` cpp
class Solution
{
    
    
    public:
    void flatten(Node *root)
    {
       if(root==NULL)return;
       if(root->left == NULL && root->right == NULL)return;
       if(root->left == NULL && root->right != NULL){flatten(root->right);return;}
       if(root->left !=NULL && root->right== NULL)
       {    flatten(root->left);
           root->right = root->left;
           root->left = NULL;
           
           return;
       }
        Node*  temp = root->right;
         flatten(root->left);
         root->right = root->left;
        root->left =NULL;
        Node* temp2 = root;
        while(temp2->right!=NULL)
        {
            temp2 = temp2->right;
        }
    flatten(temp);
    temp2->right = temp;
        
        
        
    }
};


```

### Results:  
![image](https://user-images.githubusercontent.com/64036955/187139791-b57136f1-75e5-4c21-b053-ccb3135dc142.png)
