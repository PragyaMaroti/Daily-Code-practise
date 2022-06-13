[Link](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

### Problem Statement: 
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.    
▶️ Constraints:
  
- 1 <= nums1.length, nums2.length <= 1000
- 0 <= nums1[i], nums2[i] <= 1000



## Solution 1:  
Since, the elements' value can be upto a maximum of 1000, we can take an array to count the occurences, as it provides fast access.   

```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        int n1= nums1.size();
        int n2= nums2.size();
        
        if(n1<=n2)
        {
            int hash[1001] ={0};
            
            for(int i=0; i<n1; i++)
            {
                hash[nums1[i]]++;
            }
            vector<int>ans;
            for(int i=0; i<n2; i++)
            {
                if(hash[nums2[i]]>0)
                {
                    ans.push_back(nums2[i]); hash[nums2[i]]--;
                }
            }
            return ans;
            
        }
        else{
            return intersect(nums2, nums1);
        }
    }
};
```

⏰O(N)   
🗃️ O(1 + N): O(N)   

- Results:  

![image](https://user-images.githubusercontent.com/64036955/173286554-200559b1-e21a-41c6-8434-4f6f28584b6b.png)    


### Solution 2:  With map:-   

```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        int n1= nums1.size();
        int n2= nums2.size();
        
        if(n1<=n2)
        {
            // hash[1001] ={0};
            map<int, int> hash;
            for(int i=0; i<n1; i++)
            {
               if(hash.find(nums1[i])== hash.end()){hash.insert({nums1[i], 1});}
                else hash[nums1[i]]++;
            }
            vector<int>ans;
            for(int i=0; i<n2; i++)
            {
                if(hash.find(nums2[i])!= hash.end() )
                {
                    ans.push_back(nums2[i]); 
                    hash[nums2[i]]--;
                    if(hash[nums2[i]]==0)hash.erase(nums2[i]);
                }
            }
            return ans;
            
        }
        else{
            return intersect(nums2, nums1);
        }
    }
};
```
- Results: 

![image](https://user-images.githubusercontent.com/64036955/173287805-aded91f3-9ec4-4c59-bdbb-30650e5a938e.png)   




