- Problem's link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/  
- Problem Statement:  You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.   
- Solution 1:  
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        //if(prices.size()==1)return 0;
       int max =0;
        for(int i=1; i<prices.size(); i++)
        {
            int max_p =0;
            for(int j =0 ; j<i; j++)
            {
                if(max_p < prices[i] -prices[j])
                    max_p = prices[i] -prices[j];
            }
            if(max< max_p)
                max = max_p;
        }
        return max;
    }
}
```
Performance: 
Time complexity: O(N^2)  
Correct but slow, doesn't pass all the test cases   


- Solution 2:   

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
       
  int maxProfit = 0, minPrice = INT_MAX;
		for(int i = 0; i < prices.size(); i++){
			minPrice = min(minPrice, prices[i]);
			maxProfit = max(maxProfit, prices[i] - minPrice);
		}
		return maxProfit;
    
    }
};

```

- Performance:  
![image](https://user-images.githubusercontent.com/64036955/135831816-e884bf54-b2fb-43e1-acd7-04e39cac7b6d.png)
