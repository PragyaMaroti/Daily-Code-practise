[Link](https://leetcode.com/problems/maximum-score-of-spliced-array/)

### Problem Statement:  

You are given two 0-indexed integer arrays nums1 and nums2, both of length n.

You can choose two integers left and right where 0 <= left <= right < n and swap the subarray nums1[left...right] with the subarray nums2[left...right].

For example, if nums1 = [1,2,3,4,5] and nums2 = [11,12,13,14,15] and you choose left = 1 and right = 2, nums1 becomes [1,12,13,4,5] and nums2 becomes [11,2,3,14,15].
You may choose to apply the mentioned operation once or not do anything.

The score of the arrays is the maximum of sum(nums1) and sum(nums2), where sum(arr) is the sum of all the elements in the array arr.

Return the maximum possible score.

A subarray is a contiguous sequence of elements within an array. arr[left...right] denotes the subarray that contains the elements of nums between indices left and right (inclusive).   


- Constraints:

1. n == nums1.length == nums2.length
1. 1 <= n <= 105
1. 1 <= nums1[i], nums2[i] <= 104

### Solution:  

```cpp
class Solution {
public:
    int maximumsSplicedArray(vector<int>& nums1, vector<int>& nums2) {
        int n = nums1.size();
        int sum1=0, sum2=0;
        vector<int>temp1(n);
        vector<int>temp2(n);
        
        for(int i=0; i<n; i++)
        {
            sum1 += nums1[i];
            sum2+=nums2[i];
            temp1[i] = nums2[i]-nums1[i]; // exchanged in nums1
            temp2[i] = nums1[i] - nums2[i]; // exchanged in nums2
        }
        // maximum subarray sum is to be found and then al last added to the sums1 and sums2
        
        int meh =0, msf = INT_MIN;
        for(int i=0; i<n; i++)
        {
            meh+=temp1[i];
            if(meh<temp1[i]) meh = temp1[i];
            if(msf<meh)msf = meh;
        }
        sum1 = max(sum1, sum1+msf);
        
        meh =0; msf = INT_MIN;
         for(int i=0; i<n; i++)
        {
            meh+=temp2[i];
            if(meh<temp2[i]) meh = temp2[i];
            if(msf<meh)msf = meh;
        }
        sum2 = max(sum2, sum2+msf);
        return max(sum1, sum2);
    }
};

```

-Results:  

![image](https://user-images.githubusercontent.com/64036955/175808562-d5e635c6-0ad8-4217-add3-5b9a82aad164.png)


⏰O(n)   
🗃️O(n)   


❕ [Reference for Kadane's algorithm](https://www.youtube.com/watch?v=YxuK6A3SvTs&ab_channel=TECHDOSE)




