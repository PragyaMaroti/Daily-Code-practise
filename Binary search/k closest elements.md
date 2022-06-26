[Link](https://leetcode.com/problems/find-k-closest-elements/)

### Problem Statement:  

Given a sorted integer array arr, two integers k and x, return the k closest integers to x in the array. The result should also be sorted in ascending order.

An integer a is closer to x than an integer b if:

- |a - x| < |b - x|, or   
- |a - x| == |b - x| and a < b   


- Constraints:  

1. 1 <= k <= arr.length
1. 1 <= arr.length <= 104
1. arr is sorted in ascending order.
1. -104 <= arr[i], x <= 104

### Solution:  

```cpp
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        vector<int> ans(k);
        int n = arr.size();
        if(n==k)return arr;
        if(x<=arr[0]){
            for(int i=0; i<k;i++)
                ans[i]=arr[i];
            return ans;
        }
        if(x>=arr[n-1]){
            int count=0;
            for(int i=n-k; i<=n-1; i++)
                ans[count++] = arr[i];
            return ans;
        }
        
        // general cases, requires binary search and two pointers approach
        // it will try to con
        
        int l=0; int r = n-2;
        int center ;
        while(l<=r)
        {
            int m = l+ (r-l)/2;
            if(arr[m]==x || arr[m]<x && arr[m+1]>x){center =m; break;}
            if(x> arr[m])// search right
            {
                l=m+1;
            }
            if(x<arr[m])// look left
            {
                r=m-1;
            }
            
        }
        cout<< center<<endl;
        // found the center to be looked around;
        int left = center, right = center+1; // since center can not be n-1, covered in special cases
        int count =0;
        while(count<k)//k items to be filled 
        {if(left<0)break;
         if(right>n-1)break; 
         // cases of index overflow;
        int dl = x-arr[left];
        int dr = arr[right] - x;
            if(dl<=dr){
                ans[count ++] = arr[left];
                left--;
            }
            if(dl>dr)
            {
                ans[count++] = arr[right]; right ++;
            }
        }
        if(left<0)
        {
            // stuff the right elements
            while(count<k)
            {
                ans[count++] = arr[right++];
            }
            
        }
        if(right>=n)
        {
            while(count<k)
                ans[count++] = arr[left--];
        }
        
        sort(ans.begin(), ans.end());
        return ans;
        
    }
};
```

- Results:  

[image](https://user-images.githubusercontent.com/64036955/175811339-4cae0e01-33af-4a3b-86ce-dd46723a86a4.png)

 
 
 ⏰O(log(n)) +o(k)    
 🗃️O(n)   
 
 
 
