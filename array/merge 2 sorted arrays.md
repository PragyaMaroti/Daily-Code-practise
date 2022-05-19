## Merge 2 sorted arrays

- [Link](https://leetcode.com/problems/merge-sorted-array/)


Code: 

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int n1, vector<int>& nums2, int n2) {
        if(n2==0)return ;
        if(n1==0) {nums1 = nums2; return;}
       int pointer= 0;
        int count = n1;
        for(int i=0; i<n2;i++)
        {
            while(nums1[pointer]<=nums2[i] && pointer<count)
                pointer++;
            nums1.insert(nums1.begin()+pointer, nums2[i]);
            count++;
            
        }
        // remove n1-n2 elements at the end.
        int n = nums1.size();
       
            nums1.erase(nums1.end()-(n-(n1+n2)), nums1.end());
        
        
    }
};
```
![image](https://user-images.githubusercontent.com/64036955/169256383-afdbca69-22a6-480a-84b3-a14783a7206a.png)
