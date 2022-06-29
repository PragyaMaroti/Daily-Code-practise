[Link](https://leetcode.com/problems/maximum-subarray)   

### Problem Statement:  

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.    

### Solution:  

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int max_sum = INT_MIN;
        int max_till_here =0;
        for(int i=0; i<n; i++)
        {    
            max_till_here+= nums[i];
           
            if(max_till_here<nums[i])
                max_till_here =nums[i];
           max_sum = max(max_sum, max_till_here); 
            
        }
        return max_sum;
    }
};



```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/176470543-eaeec4ac-79fa-48f8-9fa0-edb694039f3c.png)
