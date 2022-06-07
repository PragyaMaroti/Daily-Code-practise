[Link](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)  

## Problem Statement:  

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.  


```
Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Example 3:

Input: nums = [], target = 0
Output: [-1,-1]
```

Constraints:

0 <= nums.length <= 105   
-109 <= nums[i] <= 109   
nums is a non-decreasing array.   
-109 <= target <= 109    


## Solution:  

```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        
        int start =-1, end =-1;
        int n = nums.size();
        if(n==0)return {-1,-1};
        if(target<nums[0] || target> nums[n-1]) return {-1,-1};
        
        int l=0; int r= n-1;
        while(l<=r)
        {
            int m = l+ (r-l)/2;
            if(nums[m]== target){start = m; end = m; break;}
            if(nums[m]>target){r = m-1;}
            if(nums[m]<target){l =m+1;}
            
        }
        
        if(start!=-1)
        {
            while(start>=0 && nums[start]==target)start--;
            start+=1;
            if(start==1 && nums[0]==target) start--;
            while(end<n && nums[end]== target)end++;
            end--;
            if(end==n-2 && nums[n-1]== target)end++;
        }
       // vector<int> ans(2);
       // ans[0]= start;
        //ans[1]= end;
        return {start, end};
        
    }
};
```

### Results: 

![image](https://user-images.githubusercontent.com/64036955/172369808-28b6fec6-0f2f-4a27-a122-9d9cdd9a92c6.png)


⏰ O(log N) time complexity  
🗃️ O(1) space complexity
