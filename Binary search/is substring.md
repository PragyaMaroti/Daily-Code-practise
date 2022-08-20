[Link](https://leetcode.com/problems/is-subsequence/)  

### Problem Description:  

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).   





### Solution:  

```cpp
bool isSubsequence(string s, string t) {
        if(s.size()>t.size())
            return false;
        unordered_map<char,vector<int>> m;
        for(int i=0;i<t.size();i++){
            m[t[i]].push_back(i);
        }
        for(int i=0, low=-1;i<s.size();i++){
            if(m.find(s[i])!=m.end()){
                int index = lower_bound(m[s[i]].begin(), m[s[i]].end(), low+1)-m[s[i]].begin();
                if(index==m[s[i]].size())
                    return false;
                low = m[s[i]][index];
            }
            else{
                return false;
            }
        }
        return true;
    }

```
