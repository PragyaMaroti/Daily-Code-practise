- **Problem's Link**:  https://leetcode.com/problems/search-in-rotated-sorted-array/
- **Problem Statement:** 
There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.
- **Solution:**  

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.size()==1)
        {

        if(nums[0]==target)return 0;
        return -1;}
        // check if array is rotated or not
        if(nums[0]<nums[nums.size()-1])//not rotated
        {
            // do  binary search
            int l =0; int r = nums.size()-1;
            while (l <= r) {
        int m = l + (r - l) / 2;
  
     
        if (nums[m] == target)
            return m;
  

        if (nums[m] < target)
            l = m + 1;
        else
            r = m - 1;
    }

    return -1;
}
        else
        {
            // do rotated binary search with l and r, with comparison for target and ends
            
             int n = nums.size();
        int l = 0, r = n - 1;
        while(l <= r) {
            int m = l + (r - l) / 2;
            if(nums[m] == target) {
                return mid; 
            }
            if((target >= nums[0] && (nums[m] >= target || nums[m] <nums[0])) ||
               (target < nums[0] && (nums[m] < nums[0] && nums[m] >= target))) {
                r = m - 1;
            }
            else {
                l = m + 1;
            }
        }
        return -1;
    }
    }
};
```
- **Performance:**  
![image](https://user-images.githubusercontent.com/64036955/136897809-1e3426d0-f94a-4851-a159-d2c5d4c7d88d.png)
