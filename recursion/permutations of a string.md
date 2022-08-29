- [Problem's Link](https://practice.geeksforgeeks.org/problems/permutations-of-a-given-string2041/1)  


### Problem's Statement:  


Given a string S. The task is to print all unique permutations of the given string in lexicographically sorted order.   


Your task is to complete the function find_permutaion() which takes the string S as input parameter and returns a vector of string in lexicographical order.

 

Expected Time Complexity: O(n! * n)   

Expected Space Complexity: O(n)   

Constraints:
1 <= length of string <= 5
   
   
   

```cpp
Solution
{
	class public:
	    void permutate(set<string>& ans, string s, int l, int r)
	    {
	        if(l==r)
	        {
	            ans.insert(s);
	        }
	        
	        for(int i=l; i<=r; i++)
	        {
	            swap(s[l], s[i]);
	            permutate(ans, s, l+1, r);
	            swap(s[i], s[l]);
	        }
	    }
	
	
		vector<string>find_permutation(string S)
		{   int n = S.size();
		
		    set<string> ans;
		    permutate(ans, S, 0, n-1 );
		    // remove duplicates:
		   vector<string> strings;
		   
		    
		    for( string x: ans)
		    {
		        strings.push_back(x);
		    }
		    
		    
		    return strings;
		}
};
```

### Results:   

![image](https://user-images.githubusercontent.com/64036955/187169371-2e3a6e87-d0df-461e-97d7-8fc31e3fb2ee.png)
