[Link](https://leetcode.com/problems/house-robber)

### Problem Statement:  
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.


### Solution: 

```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int n = nums.size();
        if(n==1)return nums[0];
        if(n==2 )return max(nums[1], nums[0]);
        if(n==3) return max(nums[1], nums[0]+nums[2]);
        
        vector<int> dp(3);
        dp[0]= nums[0]; // if there was only 1 home
        dp[1]= max(nums[1], nums[0]);
        dp[2]=  max(nums[1], nums[0]+nums[2]);
        int ans;
        for(int i=3; i<n; i++)
        {       int temp = dp[2];
           dp[2] =  max(dp[2], dp[1]+nums[i]); // first case: not taking that ; 2nd taking that  
            dp[0] = dp[1];
         dp[1] = temp;        
        }
        return dp[2];
        
        
    }
};
```

- Results: 

![image](https://user-images.githubusercontent.com/64036955/175479084-d69dde7c-f691-4078-8180-928de6f13e01.png)
