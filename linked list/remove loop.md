- [Problem's Link](https://practice.geeksforgeeks.org/problems/remove-loop-in-linked-list/1)   

### Problem Statement:  

Given a linked list of N nodes such that it may contain a loop.

A loop here means that the last node of the link list is connected to the node at position X. If the link list does not have any loop, X=0.

Remove the loop from the linked list, if it is present.    


### Solution:  

```cpp
# include <bits/stdc++.h>
using namespace std;
class Solution
{
    public:
    //Function to remove a loop in the linked list.
    void removeLoop(Node* head)
    {
        if(head==NULL)return ;
      
        int count =0;
    Node* ptr = head;
    while(ptr!=NULL && ptr->data!= -1)
    {
       
        count++;
        ptr->data =-1;
        ptr = ptr->next;
    }
    
    if(ptr==NULL )return ; // no loop
        
    Node* slow = head;
        for(int i=0; i<count-1; i++)
        {
            slow = slow->next;
        }
        slow->next = NULL;
        return;
        
        
    }
};
```
