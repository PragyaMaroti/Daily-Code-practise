[Link](https://leetcode.com/problems/triangle/)

### Problem Statement: 
Given a triangle array, return the minimum path sum from top to bottom.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index i on the current row, you may move to either index i or index i + 1 on the next row.   

▶️ Constrints: 


- 1 <= triangle.length <= 200  
- triangle[0].length == 1    
- triangle[i].length == triangle[i - 1].length + 1   
- -104 <= triangle[i][j] <= 104   


### Solution:   

```cpp
 int minimumTotal(vector<vector<int>>& triangle) {
       int n = triangle.size();
        for(int i=n-2;i>=0;i--){
            for(int j=0;j< triangle[i].size();j++){
                triangle[i][j] += min(triangle[i+1][j], triangle[i+1][j+1]);
            }
        }
        return triangle[0][0];
    }
```
