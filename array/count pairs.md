[Link](https://practice.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1)


### Problem Description:

Given an array of N integers, and an integer K, find the number of pairs of elements in the array whose sum is equal to K.  

```
Example 1:

Input:
N = 4, K = 6
arr[] = {1, 5, 7, 1}
Output: 2
Explanation: 
arr[0] + arr[1] = 1 + 5 = 6 
and arr[1] + arr[3] = 5 + 1 = 6.

Example 2:

Input:
N = 4, K = 2
arr[] = {1, 1, 1, 1}
Output: 6
Explanation: 
Each 1 will produce sum 2 with any 1.
```


### Solution:  


```cpp
class Solution{   
public:
    int getPairsCount(int arr[], int n, int k) {
        
       // ==vector<int> array(arr, arr+n);
      //  sort(array.begin(), array.end());
        map<int, int>frequency;
        for(int i=0; i<n; i++)
        {
            if(frequency.find(arr[i])!= frequency.end())frequency[arr[i]]++;
            else frequency.insert({arr[i],1});
        }
        int count =0; 
        //int l =0; int r = n-1;
       for(int i=0; i<n; i++)
       {
           int target = k-arr[i];
           if(frequency.find(target)!=frequency.end())
           {
               if(target!=arr[i])
               {
                   count+=frequency[target];
               }
               else count+= frequency[target]-1;
           }
           
       }
        
        return count/2
        
 ```
 
 
 - Results:  

![image](https://user-images.githubusercontent.com/64036955/185898695-bc274cdc-1b07-4187-8b1c-cdc1f1215e76.png)
