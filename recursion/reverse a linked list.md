[Problem's link](https://leetcode.com/explore/learn/card/recursion-i/251/scenario-i-recurrence-relation/2378/)  
 
[Intutive reference for the approach](https://labuladong.gitbook.io/algo-en/ii.-data-structure/reverse_part_of_a_linked_list_via_recursion)  
                                      
                                      

## Recursive Solution:  
                                      
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==NULL || head->next ==NULL )return head;
        ListNode* last = reverseList(head->next);
        head->next->next = head;
        head->next= NULL;
        return last;
    }
};
```

## Iterative Approach:  

```cpp



                                      
