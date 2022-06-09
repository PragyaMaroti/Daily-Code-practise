[Link](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/)  

### Problem Statement:  

Given a m x n matrix grid which is sorted in non-increasing order both row-wise and column-wise, return the number of negative numbers in grid.  


**Constraints:**

- m == grid.length
- n == grid[i].length
- 1 <= m, n <= 100
- -100 <= grid[i][j] <= 100  

### Approach  1: Modified linear scan in each row.

```cpp
class Solution {
public:
    int countNegatives(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        int neg=0;
        int col = m-1;
        for(int i=0; i<n; i++)
        {   if(col<0)break;
            int temp = col;
        // cout<<"temp: "<<temp<<" ";
            while(col>=0 && grid[i][col]<0)col--;
            // we get the column no. of the first positive / 0 element in this row
         //cout<<"col: "<<col<<endl;   
         if(temp!=col)
            {  
               // col++;
                neg+= (temp-col)*(n-i);// these values must me negetive
             // cout<<neg<<endl;
          // col--;
            }

        }
        return neg;
    }
};
```

- **Results:**    
![image](https://user-images.githubusercontent.com/64036955/172777637-14c8f1b7-550c-408f-bee7-863cf82550d3.png)    


### Approach 2:  Binary search in each row.  

```cpp
int countNegatives(vector<vector<int>>& grid) {
         int cnt=0;
         for(int i=0;i<grid.size();i++){
             int low=0,high=grid[0].size()-1,mid;
             while(low<=high){
                 mid=low+(high-low)/2;
                 if(grid[i][mid]<0)high=mid-1;
                 else low=mid+1;
             }
             cnt+=grid[0].size()-low;
         }
        return cnt;        
    }
    
```
⏰ O(Nlog(M))
🗃️O(1)  

- **Results: **

![image](https://user-images.githubusercontent.com/64036955/172779092-81d532c8-aa88-4c65-a9f1-3c974330e8d5.png)



