- [Problem's Link](https://leetcode.com/problems/middle-of-the-linked-list/)
- Problem Statement:
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

- Solution:  

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* tomid = head;
        ListNode* toend = head;
        while( toend!=NULL && toend->next!=NULL )  // writing this condition otherwise, causes runtime error. 
        {
            toend = (toend->next->next);
            tomid = (tomid->next);
        }
        return tomid;
    }
};
```
-  Performance:   
![image](https://user-images.githubusercontent.com/64036955/142724455-fa4f48a6-d0d3-4548-995a-5d907b610cf9.png)

![image](https://user-images.githubusercontent.com/64036955/142724544-30739042-3ab7-4aeb-bb4a-f9a974127ffc.png)

![image](https://user-images.githubusercontent.com/64036955/142724548-d9683273-6c28-4a16-b0b1-f0ec9aa8c77d.png)


