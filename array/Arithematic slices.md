[Link](https://leetcode.com/problems/arithmetic-slices/)  

### Problem Statement:  

An integer array is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, [1,3,5,7,9], [7,7,7,7], and [3,-1,-5,-9] are arithmetic sequences.
Given an integer array nums, return the number of arithmetic subarrays of nums.

A subarray is a contiguous subsequence of the array.  
```
Example 1:

Input: nums = [1,2,3,4]
Output: 3
Explanation: We have 3 arithmetic slices in nums: [1, 2, 3], [2, 3, 4] and [1,2,3,4] itself.
Example 2:

Input: nums = [1]
Output: 0
``` 

-> Constraints:

- 1 <= nums.length <= 5000
- -1000 <= nums[i] <= 1000

## Solution:  

```cpp
class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& nums) {
        int n = nums.size();
        if(n<3)return 0;
        // n>=3 for arithematic array
        int l =0, r = 1, d = nums[1]-nums[0];
        int ans =0;
        while(l<n-2 && r<n)
        {   int count =2; // 2 elements as of now
         
            d = nums[r] - nums[l];
            while(r<n-1 && nums[r+1]-nums[r]==d)
            {
                r++;
                count++;
            }
        // cout<<"count: " <<count<<endl;
         if(r==n-1)
         {
             for(int i=3; i<=count; i++)
             {
                 ans+= count-i+1; //cout<<ans<<endl;
             }
             break;
         }
         else{
             for(int i=3; i<=count; i++)
             {
                 ans+= count-i+1;
             }
             l=r; r = l+1;
         }
        }
        return ans;
    }
};
```
Results:  
![image](https://user-images.githubusercontent.com/64036955/173190477-9332e920-973d-4fcb-a9ce-cbe70bae89a9.png)


⏰O(N)
🗃️O(1)
