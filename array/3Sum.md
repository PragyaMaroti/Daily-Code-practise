- [link](https://leetcode.com/problems/3sum)

### Problem Statement:  

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

**Notice that the solution set must not contain duplicate triplets.**

 

      Example 1:

      Input: nums = [-1,0,1,2,-1,-4]
      Output: [[-1,-1,2],[-1,0,1]]
      Example 2:

      Input: nums = []
      Output: []
      Example 3:

      Input: nums = [0]
      Output: []
 

Constraints:

0 <= nums.length <= 3000
-10^5 <= nums[i] <= 10^5


### Approach 1: using sets

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        set<vector<int>>temp;
        for(int i=0 ;i<n ; i++)
        {
            int sum =  nums[i];
            int j=i+1; int k=n-1;
            while(j<k)
            {
                if(nums[j]+nums[k]+ sum==0)
                {
                    vector<int> temporary = {nums[i], nums[j], nums[k]};
                    temp.insert(temporary);
                    j++;
                    k--;
                }
                else{
                    if(nums[j]+nums[k]+ sum<0)j++;
                    else k--;
                }
            }
            
        }
        // make a vector of vector to return containing all the elements in set
        vector<vector<int>>ans;
       
        for(auto it = temp.begin(); it!=temp.end(); it++)
            ans.push_back(*it);
     
        return ans;
    }
};
```
- Results:   

![image](https://user-images.githubusercontent.com/64036955/171318153-bf9c0884-a972-489e-aaa1-39355010089c.png)


### Approach 2:   


```cpp
class Solution {
public:    
    vector<vector<int>> threeSum(vector<int>& nums) {
		// make answer array
        vector<vector<int>> ans; 
		
		// corner case
        if(nums.size() < 3) return ans;
		
		// sort the array
        sort(nums.begin(), nums.end()); 
        
		// iterate over the array to fix first digit
        for (int i = 0; i < nums.size()-2; i++) 
        {    
			//we want no duplicates so we add this if
            if (i == 0 || (i > 0 && nums[i] != nums[i-1])) 
            {       
                int l = i+1, h = nums.size()-1, sum = 0 - nums[i];
                
				// now find other two elemnts in left over array
                while (l < h) {
                    if (nums[l] + nums[h] == sum) 
                    {
                        vector<int> temp = {nums[i], nums[l], nums[h]}; 
                        ans.push_back(temp);
                        
						// to avoid duplicates
                        while (l < h && nums[l] == nums[l+1]) l++;
                        while (l < h && nums[h] == nums[h-1]) h--;
                        l++; h--;
                    } 
                    else if (nums[l] + nums[h] < sum) l++;
                    else h--;
               }
            }
        }
		
		// return answer
        return ans;
    }
};
```
- Results:  

![image](https://user-images.githubusercontent.com/64036955/171317847-c2cc9a44-5880-44ed-9be5-24d177a1c851.png)
