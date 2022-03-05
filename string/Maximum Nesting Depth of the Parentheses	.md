- [Problem](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)   
- Idea: 
Counting the no. of open loops for max depth at a time, and a loop is closed when a ')' is encountered.  

- Implementation: 

```cpp
class Solution {
public:
    int maxDepth(string s) {
        // count the no. of open loops and take the max at any point
        int n = s.size();
        int n_openloop =0;
        int max_depth= 0;
        for(int i=0; i<n; i++)
        {
            if(s[i]=='(')
                n_openloop++;
            if(s[i]==')')
            {
            max_depth= max(n_openloop, max_depth);
                n_openloop --;
            }
        }
        return max_depth;
    }
};
```
- Results: 

Success Details: 
Runtime: 0 ms, faster than 100.00% of C++ online submissions for Maximum Nesting Depth of the Parentheses.
Memory Usage: 6.2 MB, less than 86.18% of C++ online submissions for Maximum Nesting Depth of the Parentheses.   



