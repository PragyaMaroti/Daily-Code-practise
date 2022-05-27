[link](https://practice.geeksforgeeks.org/problems/stickler-theif-1587115621/1#)
- involves use of dp.



- Approach 1: simple recursion, results in TLE

```cpp
int FindMaxSum(int arr[], int n)
    {
     if(n==1)return arr[n-1];
     if(n==2)return max(arr[n-2], arr[n-1]);
     if(n==3)return max(arr[n-1]+arr[n-3], arr[n-2]);
     
     int* p = arr;
     return max(arr[0]+ FindMaxSum((p+2), n-2),
      arr[1]+ FindMaxSum((p+3), n-3));
    ```
    
Approach 2: dp, storing previous max and current max values, O(n) time complexity.
```cpp
int FindMaxSum(int arr[], int n)
    {
     if(n==1)return arr[n-1];
     if(n==2)return max(arr[n-2], arr[n-1]);
     if(n==3)return max(arr[n-1]+arr[n-3], arr[n-2]);
     if(n==4)return(max(arr[n-1]+arr[n-3], arr[n-2]+arr[n-4]));
     
     int prevMax = 0;
       int currentMax = 0;
       
       for(int i = 0; i < n; i++){
           cout<<"prev: "<<prevMax<<"  curr: "<< currentMax<<endl;
           int temp = currentMax;
           currentMax = max(currentMax, prevMax + arr[i]);
           prevMax = temp;
       }
       return currentMax;
  ```
  
