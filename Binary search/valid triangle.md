[Link](https://leetcode.com/problems/valid-triangle-number/)

### Problem Statement:  

Given an integer array nums, return the number of triplets chosen from the array that can make triangles if we take them as side lengths of a triangle.

- Constraints:

1. 1 <= nums.length <= 1000
1. 0 <= nums[i] <= 1000

### Solution:  


```cpp
    class Solution {
public:
    // target = a+b and c must be less than  target
    int binary_search(vector<int>& nums, int l, int r, int target)
    {       int left = l; int right =r;
     if(nums[left]>=target)return 0;
     if(nums[right]<target)return right - left +1;
   //  int index =-1;
     
     while(l<=r)
     {
         int m = l +(r-l)/2;
         if(nums[m]<target && nums[m+1]>=target )return (m-left+1);
         if(nums[m]>=target) // we need valid values, lesser than target, so search left
         {
             r=m-1;
         }
         if(nums[m]< target){
             // since the first case has already surpassed, just search for a higher boundary
             l=m+1;
         }
     }
     // if nothing has returned till now, implies dne, which shall not happen here though, returning 0 anyways
     return 0;
           
     
    }
    int triangleNumber(vector<int>& nums) {
        int ans=0;
        int n = nums.size();
        if(n<=2)return 0;
        sort(nums.begin(), nums.end());
       // int flag =0;
        
        for(int i=0 ;i<n-2; i++)
        {       //cout<<"i: "<<i;
            int a = nums[i];
            if(a==0)continue;
            for(int j=i+1; j<n-1; j++)
            {      // cout<<" j: "<<j;
                int b = nums[j];
                if(b==0)continue;
                int count =0;
                count =  binary_search(nums, j+1, n-1, a+b);
                //cout<<"a: "<<a<<", b: "<<b<<"; count: "<< count<<endl;
                // if(count ==0){break;}
                ans+= count;
            }
//            if(flag)break;
        }
        return ans;
    }
};
                                                                        
```

- Results:    

![image](https://user-images.githubusercontent.com/64036955/175779767-1fd8d029-6592-45bd-b5f8-d1ae534dc0b8.png)   
