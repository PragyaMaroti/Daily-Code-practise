[Problem](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string)  
### Implementation:
```cpp
class Solution {
public:
    string removeDuplicates(string s) {
        stack<char> temp;
        int sz = s.size();
        string ans ="";
        for(int i=0; i<sz; i++)
        {
            if(temp.empty())
            {
                temp.push(s[i]);
            }
            else{
                if(s[i]==temp.top())
                {
                    temp.pop();
                }
                else{
                    temp.push(s[i]);
                }
            }
            
        }
        while(!temp.empty())
        {
            ans = temp.top() + ans;
            temp.pop();
        }
     
        return ans;
        
    }
};
```
Results:  
![image](https://user-images.githubusercontent.com/64036955/156978953-7a2bd42c-257e-458e-8b13-53b5dbc0b72d.png)

