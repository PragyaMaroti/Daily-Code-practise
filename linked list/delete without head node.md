- [Problem Link](https://practice.geeksforgeeks.org/problems/delete-without-head-pointer/1?page=1&category%5B%5D=Linked%20List&category%5B%5D=Stack&sortBy=submissions)  

### Problem Statement:  
You are given a pointer/ reference to the node which is to be deleted from the linked list of N nodes. The task is to delete the node. Pointer/ reference to head node is not given.     
Note: No head reference is given to you. It is guaranteed that the node to be deleted is not a tail node in the linked list.


### Solution: 

```cpp
class Solution
{
    public:
    //Function to delete a node without any reference to head pointer.
    void deleteNode(Node *del)
    {
        if(del->next->next==NULL )
    {    del->data = del->next->data;
        del->next = NULL;
        return;
    }
    
       // Your code here
     while( del->next->next!=NULL)
     
     {
         del->data= del->next->data; // 2->3; 3->4;
        //out<<del->data<<" ";
         del = del->next;
     }
     del->data = del->next->data;
        del->next = NULL;
    
    }

};
```



### Results:  

![image](https://user-images.githubusercontent.com/64036955/187132051-ca63e172-7b20-4ff6-8439-3eaa1aadefc2.png)
