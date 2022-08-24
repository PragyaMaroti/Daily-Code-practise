[Link](https://practice.geeksforgeeks.org/problems/convert-array-into-zig-zag-fashion1638/1)

### Problem Statement:   

Given an array arr of distinct elements of size N, the task is to rearrange the elements of the array in a zig-zag fashion so that the converted array should be in the below form: 

arr[0] < arr[1]  > arr[2] < arr[3] > arr[4] < . . . . arr[n-2] < arr[n-1] > arr[n].    

### Solution:  

```cpp
class Solution{
public:	
	// Program for zig-zag conversion of array
	void zigZag(int arr[], int n) {
	    // code here
	    
	   bool flag = true;
	    
	    for(int i = 0; i<n-1; i++){
	        if(flag){
	            if(arr[i]>arr[i+1]){
	                swap(arr[i], arr[i+1]);
	            }
	        }
	        else{
	            if(arr[i]<arr[i+1]){
	                swap(arr[i], arr[i+1]);
	            }
	        }
	        flag = !flag;
	}
	
	    
	}
};
```
