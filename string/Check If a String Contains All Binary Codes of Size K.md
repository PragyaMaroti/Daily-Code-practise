[Link](https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/)

### Problem Statement:
Given a binary string s and an integer k, return true if every binary code of length k is a substring of s. Otherwise, return false.

 

    Example 1:

    Input: s = "00110110", k = 2
    Output: true
    Explanation: The binary codes of length 2 are "00", "01", "10" and "11". They can be all found as substrings at indices 0, 1, 3 and 2 respectively.
    
    Example 2:

    Input: s = "0110", k = 1
    Output: true
    Explanation: The binary codes of length 1 are "0" and "1", it is clear that both exist as a substring. 
    
    Example 3:

    Input: s = "0110", k = 2
    Output: false
    Explanation: The binary code "00" is of length 2 and does not exist in the array.
 

Constraints:

- 1 <= s.length <= 5 * 10^5   
- s[i] is either '0' or '1'.   
- 1 <= k <= 20     


Approach 1: using hashing

```
class Solution {
public:
    bool hasAllCodes(string s, int k) {
        // pattern finder
       
        
        int total_combination =  1<<k;
        
        int sz =  s.size();
        
        if(total_combination > sz-k+1 )return false; // check!!
        
        vector<int> arr(total_combination, 0);
        
        
        // sliding window of size k
        for(int i=0 ; i<=sz-k; i++)
        {
            // make a substring
            string temp = s.substr(i, k); // starting from the ith element, of k size.
            // take the integer value of this string. 
          int value= bitset<8>(temp).to_ulong();
            arr[value]++;
        }
        for(int j=0; j<total_combination; j++)
        {
            if(arr[j]==0)return false;
        }
        return true;
    }
};
```
NOTE: The use of .to_ulong() to caonvert binary to unsigned long and the use of bitset<8>(temp)
Results: Fails few cases.

🌟Better Implementation of the thought:   

```cpp
class Solution {
public:
    bool hasAllCodes(string s, int k) {
        // pattern finder
       
        
     int n=pow(2,k),m=s.size();
        vector<bool>check(n,0); //Check Array ,initially all value false;
        
        int val=0; //Variable that will help in formation of binary to decimal value of every substring.
        int i=0,j=0; //Sliding window ponter.
        
        while(j<m)
        {
            val=val*2+(s[j]-'0'); //Form Binary ,Make it decimal.
            
            if(j-i+1<k) //If window size is Less than k ,just j++;
                j++;
            else if(j-i+1==k) //If we hit k size.
            {
                check[val]=true; //Mark check cval true.
                val=val-(s[i]-'0')*(pow(2,k-1)); //Remove ith value's Calucaltion .
                i++; //Increment i 
                j++; //and Increment j to maintain size of window as k
            }
        }
        
        for(int l=0;l<n;l++)
        {
            if(check[l]==false) //If we didn't find any value ,means that susbtring is missing
                return false; //Return false;
        }
        
        return true; //Return true;
    }
};
```
- Result: 
![image](https://user-images.githubusercontent.com/64036955/171312889-9f12871c-6d5e-4afa-a742-bbb5a1a18ad2.png)


Approach 2: Using sets   

```cpp
class Solution {
public:
    bool hasAllCodes(string s, int k) {
        //Edge case
	if(k > s.size()) return false;
    
    unordered_set<string> res_set;
    
	//Insertion into the set
    for(int i =0;i<= s.size()-k;i++)
        res_set.insert(s.substr(i,k));
    
	//Comparing res with 2^k
    return res_set.size() == pow(2,k);
    }
};
```
Result:   
![image](https://user-images.githubusercontent.com/64036955/171311106-1d0bdb44-4116-45bc-86d8-eb58e415eb61.png)
