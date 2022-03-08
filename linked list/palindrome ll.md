- [problem](https://leetcode.com/problems/palindrome-linked-list)
- IMplementation 1:
```cpp
**
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
    bool isPalindrome(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        stack<int>temp;
        int count =0;
        while(fast!=NULL)
        {
            temp.push(slow->val);
            slow=  slow->next;
            if(fast->next!=NULL){fast = fast->next->next; count+=2;}
            else {fast = fast->next; count+=1;}
        }
        // slow gets beyond he midpoint
        
        
        // stack filled witth first half, including midpoint
        if(count%2!=0)// odd 
            temp.pop();
        while(slow!=NULL )
        {
            if(temp.top() != slow->val)
                return false;
            else{
                temp.pop();
                slow= slow->next;
            }
        }
        return true;
        
    }
};
```
- Result: ![image](https://user-images.githubusercontent.com/64036955/157177085-31c95804-7791-45b8-8e95-6336744f4d41.png)

- Implementation 2: 
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
    bool isPalindrome(ListNode* head) {
        ListNode* p = head;
        stack<int>temp;
        while(p!=NULL)
        {
            temp.push(p->val);
            p=p->next;
        }
        // stack filled
        while(!temp.empty())
        {
            if(temp.top() != head->val)
                return false;
            else{
                temp.pop();
                head= head->next;
            }
        }
        return true;
    }
};
```
- Result: ![image](https://user-images.githubusercontent.com/64036955/157177235-09e343b1-9ed9-432a-993a-cd21fa1295c2.png)


