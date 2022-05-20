- [Link](https://leetcode.com/problems/linked-list-cycle/)
- Code: 

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        int flag = INT_MAX;
        while(head)
        {   if(head->val==INT_MAX)return true;
            head->val= INT_MAX;
            head = head->next;
        }
        return false;
        
    }
};
```
![image](https://user-images.githubusercontent.com/64036955/169519876-78ee62e0-947e-4d7c-8869-02c5fe09214c.png)
