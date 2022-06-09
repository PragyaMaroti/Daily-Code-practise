[Link](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)

### Problem Statement:
You are given an array nums of non-negative integers. nums is considered special if there exists a number x such that there are exactly x numbers in nums that are greater than or equal to x.

Notice that x does not have to be an element in nums.

Return x if the array is special, otherwise, return -1. It can be proven that if nums is special, the value for x is unique.  

**Constraints:**  

- 1 <= nums.length <= 100
- 0 <= nums[i] <= 1000



### Approach 1: Linear

```cpp
class Solution {
public:
    int specialArray(vector<int>& nums) {
        int n = nums.size();
        sort(nums.begin(), nums.end());
        int low = nums[0];
        int high = nums[n-1];
        if(n<=low)return n;
        for(int i=1; i<n; i++)
        {
            int count =0; 
            for(auto x: nums)
                if(x>=i)count++;
            if(count==i)return count;
        }
 return -1;       

    }
};
```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/172774052-0a856e23-b950-4fa5-acdf-98476bfb655b.png)


### Approach 2: Binary search

```cpp
class Solution {
public:
    int specialArray(vector<int>& nums) {
        int n = nums.size();
        sort(nums.begin(), nums.end());
        int low = 1;
        int high = n;
       // if(n<=low)return n;
        
        while(low<=high)
        {   int m = (low+high)/2;
         
            int count =0; 
            for(auto x: nums)
                if(x>=m)count++;
            if(count==m)return count;
            if(count>m)low = m+1;
            if(count<m)high = m-1;
        }
 return -1;       
        
        
        
        
        
        
        return -1;
    }
};
```

- Ressults:  

![image](https://user-images.githubusercontent.com/64036955/172773990-72842a72-a74b-418b-b367-82d7fc691a85.png)


