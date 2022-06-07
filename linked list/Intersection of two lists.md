[Link](https://leetcode.com/problems/intersection-of-two-linked-lists/)

## Problem statement:
Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

For example, the following two linked lists begin to intersect at node c1:   
![image](https://user-images.githubusercontent.com/64036955/172277876-d82f3fe8-a2b6-4e0a-964d-c81c4207581f.png)



The test cases are generated such that there are no cycles anywhere in the entire linked structure.

Note that the linked lists must retain their original structure after the function returns.

Custom Judge:

The inputs to the judge are given as follows (your program is not given these inputs):     

intersectVal - The value of the node where the intersection occurs. This is 0 if there is no intersected node.   
listA - The first linked list.     
listB - The second linked list.     
skipA - The number of nodes to skip ahead in listA (starting from the head) to get to the intersected node.   
skipB - The number of nodes to skip ahead in listB (starting from the head) to get to the intersected node.    
The judge will then create the linked structure based on these inputs and pass the two heads, headA and headB to your program. If you correctly return the intersected node, then your solution will be accepted.
    
 

Example 1:

```
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Intersected at '8'
Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
Example 2:


Input: intersectVal = 2, listA = [1,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
Output: Intersected at '2'
Explanation: The intersected node's value is 2 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [1,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.
Example 3:


Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
Output: No intersection
Explanation: From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
Explanation: The two lists do not intersect, so return null.
 
```
Constraints:

The number of nodes of listA is in the m.  
The number of nodes of listB is in the n.  
1 <= m, n <= 3 * 104  
1 <= Node.val <= 105  
0 <= skipA < m  
0 <= skipB < n  
intersectVal is 0 if listA and listB do not intersect.    
intersectVal == listA[skipA] == listB[skipB] if listA and listB intersect.   

### Approach 1:  
💡Making use of hash-array, to compare each of the nodes; **when the tail after each traversal is same**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        // intersection can't happen at 0th position ever
        // if the two pointers point to the same location at the end, then we must have an intersection
        // to find where it is, we can store the pointers in a map
        ListNode* ptrA = headA;
        ListNode* ptrB = headB;
        int a=0, b=0;
        vector<ListNode*> LA;
        vector<ListNode*>LB;
        while(ptrA!=nullptr)
        {ptrA= ptrA->next; a++; LA.push_back(ptrA);}
        while(ptrB!=nullptr)
        {ptrB=ptrB->next; b++; LB.push_back(ptrB);}
        if(ptrA==ptrB)
        {
            for(int i=0; i<b; i++)
            {
               // ListNode* temp = LB[i];
                for(int j=0; j<a; j++)
                {
                    if(LA[j]==LB[i])return LB[i];
                }
            }
        }
        return NULL;
    }
};
```

Results:   
![image](https://user-images.githubusercontent.com/64036955/172278248-baeba005-d701-4bd1-a855-c922ad0dabc6.png)   
- Could be due to the different judging criteria ig, as it ran well in dry run, tested using cout statements.   


### Solution:  

💡💡  The idea here is to traverse both the linked list and find there lengths...    
We now know that if the two linked list are equal after some point, there tails are equal and hence after that point, their lengths will also be equal...    
So, we traverse the longer linked list, till its length becomes equal to smaller linked list, and then we traverse both the linked list together and stop when there nodes are equal...   



```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *a=headA, *b=headB;
        int count1=0, count2=0;
		
		//counting lengths of both the linked list
        for(ListNode *curr=headA;curr!=NULL; curr=curr->next) count1++;
        for(ListNode *curr=headB;curr!=NULL; curr=curr->next) count2++;
        
		//If linked list 1 is longer, we traverse it, till it becomes equal to length of second...
        while(count1>count2) {
            count1--;
            a=a->next;
        }
        
		//If second one is longer, we traverse it, till it becomes equal to length of first...
        while(count2>count1) {
            count2--;
            b=b->next;
        }
        
		//Since length of both is now equal, we traverse them together, and break if the nodes become equal...
        while(a!=b) {
            a=a->next;
            b=b->next;
        }
        
        return a;
    }
};

```


