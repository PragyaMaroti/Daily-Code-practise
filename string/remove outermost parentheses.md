[Problem](https://leetcode.com/problems/remove-outermost-parentheses/)
- Idea:  keeping a track of the open loop with the count of '(' and ')' and store everything in a stack, when there are none open loops, we concatenate the ans stack with everything excecpt the first and last parentheses; until end of string.
- Implementation:  
```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        stack<char> temp;
        stack<char> temp2;
        string ans = "";
        int n = s.size();
        int open_loop =0;
        int max_depth=0;
        for(int i=0; i<n; i++)
        {
          if(s[i]=='(')
          {
             open_loop++;
              temp.push(s[i]);
          } 
            if(s[i]==')')
            {
                open_loop--;
                temp.push(s[i]);
            }
            if(open_loop==0)
            {
                temp.pop();
                while(!temp.empty())
                {
                    temp2.push(temp.top());
                    temp.pop();
                }
                temp2.pop();
            while(!temp2.empty())
            {
            ans= ans+ temp2.top();
                temp2.pop();
            }
            }
            
        }
        return ans;
    }
};
```

- Results:   
Success Details:   
Runtime: 109 ms, faster than 5.04% of C++ online submissions for Remove Outermost Parentheses.
Memory Usage: 175.4 MB, less than 5.04% of C++ online submissions for Remove Outermost Parentheses.
