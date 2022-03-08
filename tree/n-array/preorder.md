[Problem](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)

- Implementation: 

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    vector<int> ans;
    vector<int> preorder(Node* root) {
        if(root==NULL)
        {
        return ans; // no addition to list, just return
        }
        ans.push_back(root->val);
        int n = root->children.size();
        for(int i=0; i<n; i++)   // or  for(Node* child : root->children)
        {
          preorder(root->children[i]);    
        }
        return ans;
        
    }
};
```
- Results: 
- ![image](https://user-images.githubusercontent.com/64036955/157167097-ccc7687c-9f06-4559-a346-c3a481a5c075.png)

- Faster Implementation: 

```cpp
class Solution {
public:
    void preorderHelper(Node* node, vector<int> &results){
        //Add it to the results array
        results.push_back(node->val);
        //Recursilvely call on children
        for(Node* child : node->children){
            preorderHelper(child, results);
        }
    }
    
    vector<int> preorder(Node* root) {
        vector<int> results;
        if(root==nullptr){
            return results;
        }
        preorderHelper(root, results);
        return results;
    }
};
```
- Results:
- ![image](https://user-images.githubusercontent.com/64036955/157169868-bcfe1766-8a9a-49fb-9047-a2c5e8ace46c.png)

- 
