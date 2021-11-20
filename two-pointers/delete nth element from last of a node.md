- [Problem's Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
- Problem's Statement:  
- Solution:  

1.
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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
    
        // count the no. of nodes
        int count =1;
        ListNode * p =head;
        while(p->next!=NULL)
        {
            count++;
            p = p->next;
        }
        if (n==count)
        {
            // shift head
            head = head->next;
            return head;
        }
        ListNode* t =head;
        int trav = count - n; //5-2 =3, pos =3(0,1,2,3)
       // cout<<trav;
        // reach till trav -1 pos
        for(int i=0; i<trav-1; i++)
        {
            t = t->next;
        }
        // now delete the next node
        t->next = t->next->next;
        return head;
        
        
        
    }
};
```


-Performance:  
![image](https://user-images.githubusercontent.com/64036955/142725452-ea4b978e-d63d-435e-873b-087dc7c270b7.png)
![image](https://user-images.githubusercontent.com/64036955/142725460-4a1db383-8a82-4223-92f7-cfe8a2e6cf3e.png)
