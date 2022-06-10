[Link](https://leetcode.com/problems/longest-substring-without-repeating-characters)

### Problem statement: 
Given a string s, find the length of the longest substring without repeating characters.

 
```
Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
 
```
-> Constraints:

- 0 <= s.length <= 5 * 104   
- s consists of English letters, digits, symbols and spaces.   


## Solution 1: with each characer as a starting character, finding the maximum length possible.  

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
       
       
        int maxlength =1;
        int n= s.size();
        if(n<=0)return n;
        for(int i=0;i<n; i++)
        {   int length=0;
            int hash[256] ={0};
         int j=i;
            while(hash[s[j]]==0&&j<n) // appeared only once till now;
            {
                length++;
                hash[s[j++]] =1;
                
            }
       
         
         maxlength= max(length, maxlength);
         if(j>=n-1) break;
         
       //  for(int k=i;k<j; k++)
         //{  
           //  hash[s[k]] =0;

         //}
        
         
         
        }
         
        return maxlength;
    }
};
```
- Results:  

![image](https://user-images.githubusercontent.com/64036955/173092757-f4412fee-8edf-4a1b-a0ea-0ee56f3028b5.png)
   
   
### Solution 2:  Sliding window technique

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.size();
        if(n<=1)return n ;
        int l=0, r=0;
        int length =0, max_length =1;
        int hash[256]={0};
        while(l<n && r<n)
        {
            while(r<n && hash[s[r]]==0)
            {
                hash[s[r]]++;
                length++;
                r++;
            }
            //cout<<"l: "<< l<<" r: "<<r<<" length: "<<length<<endl;
            
            max_length= max(length, max_length);
            
            if(r==n-1)break;
            
            while(s[l]!=s[r])
            {
                hash[s[l]]--; l++; length--;
            }
            while(l<r && s[l]==s[r])  // imp to check l<r, otherwise the hash value length creates an issue
            {
                hash[s[l]]--; l++; length--;
            }
           // if(l>r){l=r;length =0;} // this alternative was used when l<r condition wasn't applies in 2nd loop, failed larter
           // cout<<"transformed to:"<<" l: "<<l<<" r: "<<r<<" length: "<<length<<endl;
        }
        return max_length;
        
    }
};
```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/173093750-9e59a0e1-3c1d-4c43-8bab-7ede606ef9ba.png)
- A linear time soln.   

