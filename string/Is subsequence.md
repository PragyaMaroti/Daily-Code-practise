[Link](https://leetcode.com/problems/is-subsequence/)

### Problem statement: 
Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

 -> Constraints:

- 0 <= s.length <= 100
- 0 <= t.length <= 104
- s and t consist only of lowercase English letters.


### Solution: 

```cpp
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int n =s.size();
        int m = t.size();
        if(n>m)return false;
        if(n==m) return s==t ? true: false;
        int j=0;
        int count =0;
        for(int i=0; i<n; i++)
        {
            char target = s[i];
 //           cout<<target<<": ";
            if(j>=m)break;
            for(;j<m;j++ )
            {   //cout<<j<<endl;
                if(t[j]==target){count++; //cout<<"count incremrnted to " <<count<<"for "<<t[j]<<endl;  j++;
                                 break;}
            }
        }
        return count==n? true:false;
        
    }
};
```

- Results: 
![image](https://user-images.githubusercontent.com/64036955/174514388-55eda3c1-0330-4941-a19d-c5a6acda220e.png)
