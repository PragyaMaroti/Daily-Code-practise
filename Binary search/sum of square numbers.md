[Link](https://leetcode.com/problems/sum-of-square-numbers/)


### Problem statement:  
Given a non-negative integer c, decide whether there're two integers a and b such that a2 + b2 = c.

 
 ▶️Constraints:   

0 <= c <= 231 - 1

### Solution:  

```cpp
class Solution {
public:
    bool judgeSquareSum(int c) {
        // if it is a perfect square, then the ans will be true as it can be written as sum of 0 and itself.
        if(floor(sqrt(c)) ==sqrt(c))return true;
        
           // int l = 1, r = floor(sqrt(c));
        
          long int root = sqrt(c); 
        long long int lo = 0, hi = root;
        
        while(lo <= hi) {
            if((lo*lo + hi*hi) < c)
                lo++;
            else if((lo*lo + hi*hi) > c)
                hi--;
            else
                return true;
        }   
        return false;
        
    }
};
```
- Results:  

![image](https://user-images.githubusercontent.com/64036955/173293075-bdb07013-b19d-4b96-8b0b-ddf80a884909.png)    



