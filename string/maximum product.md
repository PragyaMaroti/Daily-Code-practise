[Link](https://leetcode.com/problems/maximum-product-of-word-lengths)

## Problem statement: 
Given a string array words, return the maximum value of length(word[i]) * length(word[j]) where the two words do not share common letters. If no such two words exist, return 0.   
      Example 1:

      Input: words = ["abcw","baz","foo","bar","xtfn","abcdef"]
      Output: 16
      Explanation: The two words can be "abcw", "xtfn".
      Example 2:

      Input: words = ["a","ab","abc","d","cd","bcd","abcd"]
      Output: 4
      Explanation: The two words can be "ab", "cd".
      Example 3:

      Input: words = ["a","aa","aaa","aaaa"]
      Output: 0
      Explanation: No such pair of words.


Constraints:    

- 2 <= words.length <= 1000   
- 1 <= words[i].length <= 1000    
- words[i] consists only of lowercase English letters.   


### Approach 1: Using hash arrays

#### Attempt 1: TLE

```cpp
class Solution {
public:
    int maxProduct(vector<string>& words) {
        int ans =0;
        int sz= words.size();
        for(int i=0; i<sz-1; i++)
        {   // can't have a set as 1 word may have repeated characters.
           vector<int> hash1 (26, 0);
            
            for(int t=0; t<words[i].size(); t++)
                hash1[words[i][t]-'a']++;
            for(int j=i+1; j<sz;j++)
            {
                vector<int> hash2(26,0);
                for(int t=0; t<words[j].size(); t++)
                    hash2[words[j][t]-'a']++;
                int count=0;
                for(int i=0; i<26; i++)
                {  // cout<<"count: "<<count<<endl;
                    if(!(hash1[i] && hash2[i] ))
                        count++;
                    else break;
                        
                }
                if(count==26)
                    
                {  
                    int temp = words[i].size() * words[j].size();
                    ans = max(ans, temp);
                }
               
                
            }
            
        }
    return ans;
    }
    
};
```


#### Attempt 2: optimized, accepted
```cpp
class Solution {
public:
    int maxProduct(vector<string>& words) {
        int ans =0;
        int sz= words.size();
        for(int i=0; i<sz-1; i++)
        {   // can't have a set as 1 word may have repeated characters.
           vector<int> hash1 (26, 0);
            
            for(int t=0; t<words[i].size(); t++)
                hash1[words[i][t]-'a']++;
            
            for(int j=i+1; j<sz;j++)
            {
                vector<int> hash2(26,0);
                hash2 = hash1;
                
                int count=0;
                int n = words[j].size();
                
                for(int t=0; t<n; t++)
                {
                    if(hash2[words[j][t]-'a']==0)count++; // already not exsisting in the 1st word
                    else break;
                }
                if (count== words[j].size())
                {int temp = words[i].size() * words[j].size();
                    ans = max(ans, temp);
                }
                    
                
              
               
                
            }
            
        }
    return ans;
    }
    
};
```
- Results:   
![image](https://user-images.githubusercontent.com/64036955/170871452-1b349af4-075d-4a5c-aa21-f7154adb6b6b.png)


### Approach 2: Bit Manipulations

Concepts used:    
💡 Merging or BIT ORing.   
💡 Masking or BIT ANDing.   
💡Left shift: <<   
- [Reference for idea](https://www.udemy.com/course/datastructurescncpp/learn/lecture/13554138#overview)
```cpp
class Solution {
public:
    int maxProduct(vector<string>& words) {
        
        int res = 0;
        vector<int> bits; 
        for (int i = 0; i < words.size(); i++)
        {
            int mask = 0;
            for (int j = 0; j < words[i].length(); j++){
                mask |= 1 << (words[i][j] - 'a');
            }
            bits.push_back(mask);
        }
        for (int i = 0; i < bits.size(); i++)
        {
            for (int j = i+1; j < bits.size(); j++)
            {
                if (!(bits[i] & bits[j]))
                {
                    int prod = words[i].length()*words[j].length();
                    res = (res < prod) ? prod : res;
                }
            }
        }
        return res;
    }
};

```
-Results:
  ![image](https://user-images.githubusercontent.com/64036955/170871688-385e0274-e080-4515-b84a-12795059ba84.png)

  
