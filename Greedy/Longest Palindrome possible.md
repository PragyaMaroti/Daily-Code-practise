[Link](https://leetcode.com/problems/longest-palindrome/)

### Problem Statement:  
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

### Solution:  

```cpp
class Solution {
public:
    int longestPalindrome(string s) {
        int n = s.size();
        if(s.size()==1)return 1;
        if(s.size()==2){if(s[0]==s[1])return 2; else return 1;}
        
        vector<int> frequency(60,0); // 58 (26 +26+ extra)
        int flag = 0;
    for(int i=0; i<n; i++)
    {  
        frequency[s[i]-'A']++;
    }
        // frequency stored; now pickup all even times appearing letters and  letters that appear odd times, subtract 1 from their frequency
        int max_length =0;
       // int flag =0;
        int flag_odd =0;
        for(int i=0; i<60; i++)
        {
            if(frequency[i]>0 )
            {    if(frequency[i]>=1)flag++;
             if(frequency[i]%2!=0)flag_odd ++;
                max_length+= (frequency[i]/2 )*2;
            }
        }
        cout<<flag<<endl;
        
        if(flag==1 && flag_odd!=0)return max_length+1;
       
       if(flag_odd) return max_length+1;
        return max_length;
    }
};
```

- Results:  

