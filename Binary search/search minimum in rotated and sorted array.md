[Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array)   


### Problem Statement: 
Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:
```
[4,5,6,7,0,1,2] if it was rotated 4 times.
[0,1,2,4,5,6,7] if it was rotated 7 times.
```
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of unique elements, return the minimum element of this array.

You must write an algorithm that runs in O(log n) time.   


▶️Constraints:    

- n == nums.length   
- 1 <= n <= 5000   
- -5000 <= nums[i] <= 5000   
- All the integers of nums are **unique.**    
- nums is sorted and rotated between 1 and n times.  

### Solution:  


```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int n = nums.size();
        if(n==1)return nums[0];
        if(n==2)return min(nums[n-1], nums[0]);
        
        if(nums[0]<nums[n-1])return nums[0];
        int  l = 0; 
        int  r= n-1;
        while(l<=r)
        {   int m = l+(r-l)/2;
            if(nums[m]>=nums[0])// we are in the first increasing half yet
            {l =m+1; continue;}
         if(nums[m]<nums[0]) // we are in the second increasing half
         {
             if(nums[m]<nums[m-1])return nums[m];
             if(nums[m]>nums[m-1])r = m-1;
         }
        }
        return nums[n-1];
        
    }
};
```

- Results:  
![image](https://user-images.githubusercontent.com/64036955/173303530-565ed757-46d8-48e1-96e8-018d865e0b57.png)
