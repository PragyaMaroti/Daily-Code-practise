[Link](https://leetcode.com/problems/number-of-islands/)

### Problem Statement:  

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.



- Constraints:

1. m == grid.length
2. n == grid[i].length
3. 1 <= m, n <= 300
4. grid[i][j] is '0' or '1'.




### Solution: 


```cpp
class Solution {
public:
    void marker(vector<vector<char>>& grid, int i, int j,  int r, int c)
    {
        if(grid[i][j]!='1' )return ;
        grid[i][j]='0';
        if(i>0){marker(grid, i-1, j, r, c);}
        if(i<r-1){marker(grid, i+1, j, r, c);}
        if(j>0){marker(grid, i, j-1, r, c);}
        if(j<c-1){marker(grid, i, j+1, r, c);}
    }
    int numIslands(vector<vector<char>>& grid) {
        int r = grid.size();
        int c = grid[0].size();
        int count =0;
        for(int i=0; i<r; i++)
        {
            for(int j=0;j<c;j++)
            {
                if(grid[i][j]=='1')
                {
                    marker(grid, i, j, r, c);
                    count++;
                }
            }
        }
        return count;
    }
};
```


- Results:  

![image](https://user-images.githubusercontent.com/64036955/175812351-6822fbf9-6fa9-4a0c-b1f2-8f08bf8511d0.png)
