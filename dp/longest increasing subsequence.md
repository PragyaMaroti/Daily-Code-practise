[Link](https://leetcode.com/problems/longest-increasing-subsequence/)  

### Problem Statement:  

Given an integer array nums, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].   


- Constraints:

1. 1 <= nums.length <= 2500   
2. -104 <= nums[i] <= 104   

### Solution: using DP:  

```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int  n = nums.size();
        vector<int> temp (n,1);
        
        for(int i=1; i<n; i++)
        {
            
            for(int j=0; j<i; j++)
            {
                if(nums[i]>nums[j] && temp[i]<=temp[j])
                {
                    temp[i] =  temp[j]+1;
                }
            }
        }
        int ans =1;
        for(int i=0; i<n; i++)
        if(temp[i]>ans)ans=  temp[i];
        return ans;
    }
};
```

- Results:  
![image](https://user-images.githubusercontent.com/64036955/175818913-4e06d022-375b-45ce-9090-0b1f7d8f6bdc.png)
