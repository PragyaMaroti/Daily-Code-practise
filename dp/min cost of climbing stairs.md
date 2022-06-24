[Link](https://leetcode.com/problems/min-cost-climbing-stairs/)  

### Problem Statement:  

You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.


### Solution:  

```cpp
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        int n= cost.size();
        if(n==2)return min(cost[0], cost[1]);
    vector<int> min_to_reach(n);
       min_to_reach[0] = cost[0];
        min_to_reach[1] = cost[1];
        min_to_reach[2] =  min(min_to_reach[0]+ cost[2], min_to_reach[1]+cost[2]);
    
        
     for(int i=3; i<n; i++)
    {
       min_to_reach[i] = min(min_to_reach[i-1], min_to_reach[i-2])+cost[i];
    }
    
        return min(min_to_reach[n-1], min_to_reach[n-2]);
    }
};
```

⏰ O(n)
🗃️ O(n)

- Results: 

![image](https://user-images.githubusercontent.com/64036955/175516565-ad76d0e6-3947-4f8b-a73f-628fb10964fc.png)

