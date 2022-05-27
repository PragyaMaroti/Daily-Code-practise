[Link](https://practice.geeksforgeeks.org/problems/find-all-four-sum-numbers1732/1#)
## Problem Statement:
Given an array of integers and another number. Find all the unique quadruple from the given array that sums up to the given number.

returns an array containing all the quadruples in a lexicographical manner. Also note that all the quadruples should be internally sorted, ie for any quadruple [q1, q2, q3, q4] the following should follow: q1 <= q2 <= q3 <= q4.  (In the output each quadruple is separate by $. The printing is done by the driver's code)

Expected Time Complexity: O(N^3).
Expected Auxiliary Space: O(N^2).

Constraints:
1 <= N <= 100
-1000 <= K <= 1000
-100 <= A[] <= 100


### Code:

⭐use of set for uniquness

```cpp
class Solution{
    public:
    // arr[] : int input array of integers
    // k : the quadruple sum required
    vector<vector<int> > fourSum(vector<int> &arr, int k) {
        int n=arr.size();
       sort(arr.begin(),arr.end());
      
       set<vector<int>>ans;
       
       for(int i=0;i<=(n-3);i++){
           for(int j=i+1;j<=(n-2);j++){
               int sum=arr[i]+arr[j];
               int l=j+1,r=n-1;
               while(l<r){
                    if(sum+arr[l]+arr[r]==k){
                       ans.insert({arr[i],arr[j],arr[l],arr[r]});
                       l++;
                       r--;
                   }
                   else if(sum+arr[l]+arr[r]>k) r--;
                   else l++;
               }
           }
       }
       vector<vector<int>>vec;
       for(auto it=ans.begin();it!=ans.end();it++){
           vec.push_back(*it);
       }
       return vec;
    }
};
```
![image](https://user-images.githubusercontent.com/64036955/170682826-e3578ceb-defb-401c-b59b-c53363559578.png)
