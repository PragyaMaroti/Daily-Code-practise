[Problem](https://leetcode.com/problems/n-ary-tree-postorder-traversa)


-Implementation:
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
    void postorderhelp(Node* root, vector<int>& ans)
    {
        for(auto child : root->children)
        {
            postorderhelp(child, ans);
        }
        ans.push_back(root->val);
    }
    vector<int> postorder(Node* root) {
        vector<int> ans;
        if(root==nullptr)
            return ans;
        postorderhelp(root, ans);
        return ans;
            
    }
};

```
- Results:
![image](https://user-images.githubusercontent.com/64036955/157171061-0ee480e1-31ea-4b5c-b344-d7dcc574737b.png)


- Implementation 2: 

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
    vector<int>ans;
    void postorderhelp(Node* root)
    {
        for(auto child : root->children)
        {
            postorderhelp(child);
        }
        ans.push_back(root->val);
    }
    vector<int> postorder(Node* root) {

        if(root==nullptr)
            return ans;
        postorderhelp(root);
        return ans;
            
    }
};

```
- Results:
- ![image](https://user-images.githubusercontent.com/64036955/157171330-0e3ca2bb-bcb4-4488-8a1e-0e459514e6ca.png)
