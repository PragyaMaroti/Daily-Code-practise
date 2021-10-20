## Method 1:  
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()==0)return 0;
        if(nums.size()==1)return 1;
        for(int i=0; i<nums.size()-1; i++)
        {
            if(nums[i]==nums[i+1])
            {
                nums.erase(nums.begin()+i);
                i--;
            }
        }
        
        return nums.size();
        
    }
};
```

**Runtime: 690 ms**, faster than 5.83% of C++ online submissions for Remove Duplicates from Sorted Array.    
**Memory Usage: 18.3 MB**, less than 74.43% of C++ online submissions for Remove Duplicates from Sorted Array.     

## Method 2:  (Faster) 
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()==0 || nums.size()==1 )return nums.size();
       int index =1;
        for(int i=1; i<nums.size();i++)
        {
            if(nums[i]!=nums[i-1])
                nums[index++] = nums[i];
        }
        return index;
    }
};
```
**Runtime: 4 ms**, faster than 99.02% of C++ online submissions for Remove Duplicates from Sorted Array.
**Memory Usage: 18.4 MB**, less than 74.43% of C++ online submissions for Remove Duplicates from Sorted Array.
