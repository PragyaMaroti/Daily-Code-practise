[Link](https://leetcode.com/problems/longest-common-subsequence/)


### Problem statement:  

Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

    
- Constraints:

1. 1 <= text1.length, text2.length <= 1000   
1. text1 and text2 consist of only lowercase English characters.      
    
### Solution:  

```cpp
class Solution {
public:
    int longestCommonSubsequence(string s1, string s2) {
        if(s1.size()==0 || s2.size()==0)return 0;
        if(s1==s2)return s1.size();
       int n1 = s1.size(), n2 = s2.size();
        vector<vector<int>>dp(n2+1, vector<int>(n1+1, 0));
      
        for(int i=1; i<n2+1; i++)// rows
        {
            
            for(int j=1; j<n1+1; j++) // cols
            {      
                if(s1[j-1]==s2[i-1]) // item to be included in lcs
                   dp[i][j] = 1 + dp[i-1][j-1];
                else{
                    dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
                }
            
                    
            }
        }
        
        
        
        return dp[n2][n1];
    }
};

```
- Results:   

