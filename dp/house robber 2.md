[Link](https://leetcode.com/problems/house-robber-ii)   

### Problem statement:  

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.


### Solution:  

```cpp
class Solution {
public:
    
    int rob_helper(vector<int>& nums) {
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
    int rob(vector<int>& nums) {
        int n = nums.size();
        if(n==1)return nums[0];
        if(n==2) return max(nums[0], nums[1]);
        if(n==3)return max(max(nums[0], nums[1]), nums[2]);
        
        // taking two cases of including only the 1st one, 2nd of taking only the last element
        vector<int> temp1(nums.begin(), nums.end()-1);
        vector<int> temp2(nums.begin()+1, nums.end());
        int ans1 = rob_helper(temp1);
        int ans2 =  rob_helper(temp2);
        return max(ans1, ans2);
        
        
    }
};
```

- Results:   
![image](https://user-images.githubusercontent.com/64036955/175481958-a2941006-66c9-4b18-880a-c43292c799e5.png)
