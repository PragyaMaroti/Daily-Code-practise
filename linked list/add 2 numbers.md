## Add 2 numbers

[link](https://leetcode.com/problems/add-two-numbers/)

- Problem: 
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.   
![image](https://user-images.githubusercontent.com/64036955/168949291-7b1b0245-b5bb-4c42-a87f-f6d9148313d1.png)


- Solution:
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) { 

if(!l2&&!l2)
                    return NULL;
       
         ListNode*  temp=new ListNode(0);
          ListNode* head=temp;
            int carry=0;
            while(l1||l2||carry)
            {
                    int sum=0;
                    if(l1)
                    {
                            sum+=l1->val;
                            l1=l1->next;
                    }
                    if(l2)
                    {
                            sum+=l2->val;
                            l2=l2->next;
                    }
                    sum+=carry;
                    carry=sum/10;
                    ListNode * x=new ListNode(sum%10);
                    temp->next=x;
                    temp=temp->next;
            }
            head=head->next;
           
            return head;
    }
};
```


```
while(l1||l2||carry)
```
this was a crucial conditions otherwise, it was needed to wrote 3 conditions to get every case
