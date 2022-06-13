[Link](https://practice.geeksforgeeks.org/problems/remove-duplicate-element-from-sorted-linked-list/1#)

### Problem Statement:  
Given a singly linked list consisting of N nodes. The task is to remove duplicates (nodes with duplicate values) from the given list (if exists).
Note: Try not to use extra space. Expected time complexity is O(N). The nodes are arranged in a sorted way.   

Expected Time Complexity : O(N)   
Expected Auxilliary Space : O(1)   

Constraints:   
1 <= Number of nodes <= 104    

## Solution:  

```cpp
Node *removeDuplicates(Node *head)
{
    
     Node* ptr = head;
     if(ptr==NULL)return head;
     if(ptr->next==NULL)return head;
     while(ptr!=NULL)
     {
         int curr = ptr->data;
         while(ptr->next!=NULL && ptr->next->data == curr)
         {
             ptr->next = ptr->next->next;
         }
         ptr = ptr->next;
         
     }
     return head;
}
```

- Results:   
![image](https://user-images.githubusercontent.com/64036955/173383893-78058fd2-b6ab-447c-91da-bcc952fa17fa.png)
