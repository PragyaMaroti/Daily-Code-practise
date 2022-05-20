- [Link](https://leetcode.com/problems/counting-bits)

```cpp
class Sol
  ution {
public:
    vector<int> countBits(int n) {
        vector<int> ans(n+1,0);
        for(int i=0; i<=n;i++)
        {
          for(int j=0; j<18 ; j++)
          {
              if(i & 1<<j)ans[i]++;
          }
        }
        return ans;
    }
};
```



```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        if(n == 0) return {0};
        vector<int> dp(n + 1);
        
        dp[0] = 0; dp[1] = 1;
        
        for(int i = 2; i <= n; i++) {
            if(i % 2 == 0) 
				dp[i] = dp[i / 2];
            else 
				dp[i] = 1 + dp[i / 2];
        }
        return dp;
    }
};
```

![image](https://user-images.githubusercontent.com/64036955/169508301-a7bb686b-d3a5-4e9d-8030-b541e90fb5f1.png)
