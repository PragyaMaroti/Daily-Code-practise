[Link](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)  

## Problem statement:
You are given an integer array nums and an integer x. In one operation, you can either remove the leftmost or the rightmost element from the array nums and subtract its value from x. Note that this modifies the array for future operations.

Return the minimum number of operations to reduce x to exactly 0 if it is possible, otherwise, return -1.

 
```
Example 1:

Input: nums = [1,1,4,2,3], x = 5
Output: 2
Explanation: The optimal solution is to remove the last two elements to reduce x to zero.
Example 2:

Input: nums = [5,6,7,8,9], x = 4
Output: -1
Example 3:

Input: nums = [3,2,20,1,1,3], x = 10
Output: 5
Explanation: The optimal solution is to remove the last three elements and the first two elements (5 operations in total) to reduce x to zero.
``` 

-> Constraints:

- 1 <= nums.length <= 105
- 1 <= nums[i] <= 104
- 1 <= x <= 109


## Solution:   

![image](https://user-images.githubusercontent.com/64036955/173184477-1bb04ea0-4316-475c-8b99-2f670b62cc10.png)

Solution I - Sliding Window [Accepted]

We need to make prefix_sum + suffix_sum = x. But instead of this, finding a subarray whose sum is sum(nums) - x will do the job. Now we only need to maximize the length of this subarray to minimize the length of prefix + suffix, which can be done greedily. By doing this, we can get the minimum length, i.e., the minimum number of operations to reduce x to exactly 0 (if possible).

-> steps:   

1. Let us take a sliding window whose ends are defined by start_idx and end_idx.
2. If the sum of this sliding window (subarray) exceeds the target, keep reducing the window size (by increasing start_idx) until its sum becomes <= target.
3. If the sum becomes equal to the target, compare the length, and store if it exceeds the previous length.
4. Return -1 if the sum of the sliding window never becomes equal to target.   

```cpp
class Solution {
   public:
    int minOperations(vector<int>& nums, int x) {
        int sum = 0, n = nums.size();
        for (int i : nums) sum += i;
        int target = sum - x;
        int curr_sum = 0, max_len = 0;
        int start_idx = 0;
        bool found = false;
        for (int end_idx = 0; end_idx < n; end_idx++) {
            curr_sum += nums[end_idx];
            while (start_idx <= end_idx && curr_sum > target) {
                curr_sum -= nums[start_idx];
                start_idx += 1;
            }
            if (curr_sum == target) {
                found = true;
                max_len = max(max_len, end_idx - start_idx + 1);
            }
        }
        return found ? n - max_len : -1;
    }
};
```

- Time Complexity: O(n)
- Space Complexity: O(1)   

- Results:   
![image](https://user-images.githubusercontent.com/64036955/173184558-befaf901-4357-4645-a261-400ef5b1229f.png)


