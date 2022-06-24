[Link](https://leetcode.com/problems/jump-game)

### Problem Statement:  

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.   


### Solution:  

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
     int reach = 0;
        
        for(int i = 0 ; i <= reach ; i++){
            reach = max(reach, i + nums[i]);
            if(reach >= nums.size() - 1){
                return true;
            }
        }
        return false;
        
    }
};
```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/175545522-11a8e84e-0e74-437f-a035-6bdd47749f0f.png)
