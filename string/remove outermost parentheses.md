[Problem](https://leetcode.com/problems/remove-outermost-parentheses/)
- Idea:  keeping a track of the open loop with the count of '(' and ')' and store everything in a stack, when there are none open loops, we concatenate the ans stack with everything excecpt the first and last parentheses; until end of string.
- Implementation: 
    1. Using stack: 
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


   2. Using queue: 

```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
       queue<char> temp;
        string ans = "";
        int n = s.size();
        int open_loop =0;
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
                int sz =  temp.size()-1;
                for(int i=0; i<sz; i++)
                {
                    ans = ans+ temp.front();
                    temp.pop();
                }
                temp.pop();
            }
            
        }
        return ans;
    }
};
```
   - Results:

Success Details:  
Runtime: 94 ms, faster than 5.04% of C++ online submissions for Remove Outermost Parentheses.
Memory Usage: 175.5 MB, less than 5.04% of C++ online submissions for Remove Outermost Parentheses.

   
   3. Without stack / queue:  

```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        int n = s.size();
        string ans = "";
        int open_loop =0;
        for(int i=0; i<n; i++)
        {
            if(s[i]=='(')
            {
                if(open_loop==0)
                    open_loop++;
                else{
                    ans = ans + s[i];
                    open_loop++;
                }
            }
            if(s[i]==')')
            {
            open_loop--;
            if(open_loop!=0)
            {
                ans = ans+ s[i];
            }
    
    
            }
        }
        return ans;
    }
};
```

Success Details: 
Runtime: 16 ms, faster than 14.76% of C++ online submissions for Remove Outermost Parentheses.
Memory Usage: 175.3 MB, less than 5.04% of C++ online submissions for Remove Outermost Parentheses.
