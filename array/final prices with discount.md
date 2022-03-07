[problem](https://leetcode.com/problems/final-prices-with-a-special-discount-in-a-shop/)
### Implementation:
```cpp
class Solution {
public:
    vector<int> finalPrices(vector<int>& prices) {
       
        int n = prices.size();
       // vector<int> ans(n);
        
        for(int i =0; i<n; i++)
        {   //ans[i]= prices[i];
            for(int j=i+1 ;j<n; j++)
            {
                if(prices[j]<= prices[i])
                {
                    prices[i] = prices[i]- prices[j];
                    break;
                }
                
            }
            
        }
        return prices;
    }
};
```
### Result: 
![image](https://user-images.githubusercontent.com/64036955/156971709-a4ab8c40-64da-4414-b15f-cdd16ac55c70.png)
