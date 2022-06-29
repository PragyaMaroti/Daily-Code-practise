[Link](https://leetcode.com/problems/jump-game-ii/)

### Problem Statement

Given an array of non-negative integers nums, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

**You can assume that you can always reach the last index.**   

### Solution:  

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int count =0;
        int n = nums.size();
        if(n==1)return 0;
        for(int i=0; i<n;)
        {   cout<<i<<endl;
            if(i+nums[i]>=n-1)return count+1;
            int reach = 0;
            int max_pos = -1;
            for(int j=1; j<=nums[i]; j++)
            {
                if(nums[i+j]+(i+j)>reach)
                {
                    max_pos =j+i;
                    reach = nums[i+j]+i+j;
                } 
                
            }
             i = max_pos;
            count+=1;
        }
        return count;
        
    }
};

```
![image](https://user-images.githubusercontent.com/64036955/176467000-afded945-b617-41e6-bd4c-54370754e04c.png)
