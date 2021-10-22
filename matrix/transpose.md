- [Problem's Link](https://leetcode.com/problems/transpose-matrix/)
- Problem Statement: 
Given a 2D integer array matrix, return the transpose of matrix.

The transpose of a matrix is the matrix flipped over its main diagonal, switching the matrix's row and column indices.
- Solution:  

```cpp
class Solution {
public:
    vector<vector<int>> transpose(vector<vector<int>>& matrix) {

int nrows = matrix.size(), ncols = matrix[0].size();
        
        vector<vector<int>> ans;
        
       for(int i=0; i<ncols; i++)
       { vector<int> temp;
           for(int j=0; j<nrows; j++)
               temp.push_back(matrix[j][i]);
               ans.push_back(temp);
       }
        return ans;
            
    }
};
```

- Performance: 
![image](https://user-images.githubusercontent.com/64036955/138475997-f39cf86a-2e2c-4427-b203-29584bd8961e.png)
