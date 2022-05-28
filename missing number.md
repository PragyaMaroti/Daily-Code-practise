[Link](https://leetcode.com/problems/missing-number/)

## Problem Statement: 
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

 

Example 1:

    Input: nums = [3,0,1]
    Output: 2
    Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.
    Example 2:

    Input: nums = [0,1]
    Output: 2
    Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.
      Example 3:

      Input: nums = [9,6,4,2,3,5,7,0,1]
      Output: 8
      Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.
 

- Constraints:  

n == nums.length  
1 <= n <= 10^4    
0 <= nums[i] <= n   
All the numbers of nums are unique.  


### Approach 1: simple sorting and array traversal

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        if(nums[0]!=0)return 0;
        else{
            for(int i=1; i<n; i++)
            {
                if(nums[i]!=nums[i-1]+1)return nums[i-1]+1;
            }
        }
        return n;
    }
};
```
Time complexity: O(nlogn)
space complexity = O(1)

- results

![image](https://user-images.githubusercontent.com/64036955/170827613-262f14b1-6859-44b5-b901-30195c99fa7f.png)


### Approach 2: Math based

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int sum = (n*(n+1))/2;
        int temp_sum=0;
        for(int i=0; i<n; i++)
        {
            temp_sum+=nums[i];
        }
        return sum-temp_sum;
    }
};
```
Time complexity: O(n);   
Space complexity: O(1);   

- Results:  

![image](https://user-images.githubusercontent.com/64036955/170827668-25d2de64-56df-46a2-aa11-c17bf1ef8e37.png)


### Approach 3: Inplace swapping

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int ans =n;
        for(int i=0; i<n; i++)
        {
           while(nums[i] != n and nums[i] != i){
                swap(nums[i], nums[nums[i]]);
        }
        }
        for(int i=0; i<n; i++)
        {
            if(nums[i]!=i)return i;
        }
        return ans;
    }
};
```
Time complexity: O(n)    
Space complexity: O(1)   

- Results:    

![image](https://user-images.githubusercontent.com/64036955/170827752-5aa1535d-dbca-4ff1-8a6d-dae213ec5c94.png)    


### Approach 4: Bit manipulation using XOR
```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        // xor based approach:
        //x^0 =x
        // x^x =0
        int n = nums.size();
       
        int total_sum =0;
        for(int i=0; i<=n; i++)
        {
           total_sum= total_sum^i;
        }
        
        for(int i=0; i<n; i++)
        {
           total_sum= total_sum ^nums[i];
        }
        
        
        return total_sum;
    }
};

```
Time complexity: O(n)    
Space complexity: O(1)   

- Results:   

![image](https://user-images.githubusercontent.com/64036955/170827804-18f97477-4f09-4239-8dff-0aedb752e6c6.png)


