[Link](https://practice.geeksforgeeks.org/problems/kth-smallest-element5635/1#)

## Approach 1: Using STL
```cpp
int kthSmallest(int arr[], int l, int r, int k) {
        //code here
        vector<int> temp(r-l+1);
        for(int i=0; i<=r; i++)
        temp[i]= arr[i];
        sort(temp.begin(), temp.end());
        return temp[k-1];
   
    }
```

## Approach 2: Binary search 

```cpp
class Solution{
    public:
    // arr : given array
    // l : starting index of the array i.e 0
    // r : ending index of the array i.e size-1
    // k : find kth smallest element and return using this function
    
    int count(int arr[], int sz, int target)
    {   int c=0;
        for(int i=0; i<sz; i++)
        if(arr[i]<= target) c++;
        
        return c;
    }
    int kthSmallest(int arr[], int l, int r, int k) {
        //code here
        int sz = r-l+1;
       int low = arr[l];
       int high = arr[r];
       for(int i =l+1; i<r; i++)
       {
           low = min(low, arr[i]);
           high = max(high , arr[i]);
           
       }
       while(low<high)
       {
           int mid= (low+high)/2;
           if(count(arr, sz, mid)<k)
           low = mid+1;
           else high = mid;
       }
        return low;
    }
};
```
