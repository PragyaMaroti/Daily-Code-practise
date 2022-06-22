[Link](https://leetcode.com/problems/kth-largest-element-in-an-array)

### Problem statement:  
Given an integer array nums and an integer k, return the kth largest element in the array.

Note that it is the kth largest element in the sorted order, not the kth distinct element.    

- Constraints:

1. 1 <= k <= nums.length <= 104    
2. -104 <= nums[i] <= 104    

### Trivial solution: 

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        int n = nums.size();
        //int pivot = k;
        //int p1=0; int p2 =n-1;
            for(int i=n-1; i>=n-k; i--)
            {
                for(int j=0; j<i; j++)
                {
                    if(nums[i]<nums[j])
                    {
                        // swap
                        int temp =  nums[i];
                        nums[i]=nums[j];
                        nums[j] = temp;
                        
                    }
                }
               // cout<<i<<"th: "<< nums[i]<<" ";
            }
        return nums[n-k];
        
    }
};
```








- Results:  
 ![image](https://user-images.githubusercontent.com/64036955/175041873-d8722606-2021-4908-92a1-94bc3cd17915.png)



