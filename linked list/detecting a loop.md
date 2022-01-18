- [Link](https://practice.geeksforgeeks.org/problems/detect-loop-in-linked-list/1#)
- Description: 
The task is to check if the linked list has a loop. Linked list can contain self loop.   
- Solution:  

```cpp
class Solution
{
    public:
    //Function to check if the linked list has a loop.
    bool detectLoop(Node* head)
    {
        Node* p = head;
        while(p!=NULL)
        {   if(p->data== INT_MAX) return true;
            p->data = INT_MAX;
            p =  p->next;
            
        }
        return false;
    }
}; 

```

 Using sets:  
 
 ```cpp
 class Solution
{
    public:
    //Function to check if the linked list has a loop.
    bool detectLoop(Node* head)
    {   Node* p = head;
       set<Node*> marking;
       marking.insert(head);
       p= p->next;
       while(p!=NULL)
       {
           if(marking.find(p) != marking.end()) return true;
           marking.insert(p);
           p=p->next;
       }
       return false;
    }
};
```
- failed with two pointers method
