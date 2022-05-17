## Moore's Voting Algorithm. 
[Reference video](https://www.youtube.com/watch?v=n5QY3x_GNDg)
### Steps:
1. Assume that the first algorithm is our majority element. Maintain the ME(majority element) and its count(=1, as initialized).
2. Majority element implies that the occurance of that element must be greater thar (N/2) where N is the number of elements in the array.
3. TO do: as we traverse throug the array, when the ME is not same as next element, we decrement the count by 1 till we reach the last element. 
4. if the count becomes 0 at a point, we change the ME value as the current value and proceed.
5. When reached the end, we shall have a value for ME. 
6. Verify the ME value by going through the array and checking its count, whether it fits the criteria or not.

This method works because, only for majority elements(count>N/2) it will be possible to have its count value more than 0 till the end, or it will be simply an element at the end, for which we do checking part.

Time complexity :O(N)
Space complexity: O(1)


- [Problem Link](https://leetcode.com/problems/majority-element/submissions/)

- Code: 
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size();
        int threshold = n/2;
        int ME = nums[0];
        int count =1;
        for(int i=1; i<n; i++)
        {
            if(ME!=nums[i])count--;
            else count++;
        if(count ==0) {ME = nums[i];    count =1;}
        }
      // the checking part isn't required in this particular qn as, it assumes there will be a majority element always.
       /* int counter=0;
         for(int i=0; i<n; i++)
         {
             if(nums[i]==ME)
                 counter ++;
         }*/
        //if(counter>threshold) 
            return ME;
       // else return -1;
    }
};
```

![image](https://user-images.githubusercontent.com/64036955/168716411-477919cf-3a20-4959-a5ca-98bdb75918c5.png)   
- [X] [follow-up problem](https://leetcode.com/problems/majority-element-ii)
