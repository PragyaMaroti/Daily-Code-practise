[Link](https://leetcode.com/problems/add-two-numbers)

Description:  

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.   

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode;   // new is an operator which calls thet constructor of ListNode , as shown in its description, has 3 forms and then memory is dynamically allotted for the pointer to point.
        ListNode* ans; // a pointer to keep track of the answer list
         ans = dummy; //ans is now pointing to dummy, which will be further pointing to the list elements' sum
        ListNode* p =l1; ListNode*q = l2; // tracking the two lists
        int carry =0;
        while(p!=NULL || q!=NULL) // while both of them are non-empty
        {
            int a  = (p!=NULL)? p->val: 0;
            int b = (q!= NULL)? q->val:0;
            int sum = a+b+carry;
            
                carry = sum/10; // notewortthy, no ifs are needed here
                sum = sum%10;
                
                ListNode* temp = new ListNode(sum);
                dummy->next = temp;
                dummy= dummy->next;
            if(p!=NULL) p= p->next;
            if(q!=NULL) q= q->next;
                
        }
        if(carry >  0)
        {
            dummy->next = new ListNode(carry); // the constructor form!
        }
        return ans->next; // cuz ans is pointing to dummy and dummy is pointing to a node of value 0
      // needed because if we do not allocate a memory before, it will not be pointing anywhere, then head will not have a specific location, while returning, it won't return anything
      
    }
};
```


![image](https://user-images.githubusercontent.com/64036955/149715012-65ce27ea-c3de-422a-853a-faa53016c6e1.png)


if the 
