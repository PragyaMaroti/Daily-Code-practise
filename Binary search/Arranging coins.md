[Link]()

## Problem Statement: 
You have n coins and you want to build a staircase with these coins. The staircase consists of k rows where the ith row has exactly i coins. The last row of the staircase may be incomplete.

Given the integer n, return the number of complete rows of the staircase you will build.   

- Constraint:
1 <= n <= 231 - 1

## Solution: 

As a reminder, the constraint of the problem can be expressed as follows:
![image](https://user-images.githubusercontent.com/64036955/173332754-ad3797f9-3fa7-467c-b333-f92b49616b16.png)

```cpp
class Solution {
public:
    int arrangeCoins(int n) {
        return (int)(sqrt(2* long(n)+ 0.25)-0.5);
    }
};
```
- Results: 

![image](https://user-images.githubusercontent.com/64036955/173332867-421f6894-3291-451e-a927-d5bd15ffd82f.png)


## Using Binary search
```cpp
class Solution {
public:
    int arrangeCoins(int n) {
        // int l=0; int r = n;
        if(n<=2)return 1;
        if(n==3)return 2;
        
      //  vector<int>running_sum(n+1);
       // running_sum[0]=0;
        //running_sum[1] =1;
        //for(int i=2; i<n+1; i++)
        
        //    running_sum[i] = running_sum[i-1]+ i;
        
        int l =0, r = n;
        while(l<=r)
        {
           long long  int m = l+ (r-l)/2;
            long long int curr = (m*(m+1))/2;
            if(curr==n|| curr<n && (curr+m+1)>n) return m;
            if(curr<n) l=m+1; // searching right
            if(curr>n)r=m-1; // searching left
        }
        return -1;
    }
};
```
-Results:  
![image](https://user-images.githubusercontent.com/64036955/173334129-b5197583-50b0-4f75-9457-1bfcb34e6bba.png)    

