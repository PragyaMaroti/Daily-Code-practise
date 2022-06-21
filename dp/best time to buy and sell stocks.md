[Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)   

### Problem Statement:  
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.



## Solution:  

- Trial 1:  

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int max_profit=0;
        int max_from_here = 0;
        int max_pos = -1;
        for(int i=0; i<n; i++)
        {
            int curr = prices[i];
            if(max_pos>i)
            {
                // case where we have already found max_element and just difference is needed
                max_profit = max(max_profit, max_from_here - curr);
            }
            else{
                // now, we gotta look for the maximum in remaining array
                int temp_max = prices[i]; // current is maximum, also covering cases of no element being smaller than it;
                int temp_pos =  i;
                for(int j=i+1; j<n; j++)
                {   
                    if( prices[j]>temp_max)
                    {temp_max = prices[j];  temp_pos = j;}                
                }
                
           max_from_here  = temp_max;
                max_pos = temp_pos;
            //cout<<i<<": "<<" max_from_here is "<<  max_from_here<< "at pos "<< max_pos<<endl;
                max_profit = max(max_profit, max_from_here- prices[i]);
              //  cout<< "max_ profit yet is: "<< max_profit<< endl;
           
            }
        }
        return max_profit;
    }
};
```

Result:  
![image](https://user-images.githubusercontent.com/64036955/174818822-a3fbc766-f461-4c89-89a6-c656f90171e6.png)



- Optimized solution using DP:  

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<int> max_elem(n,-1);
        max_elem[n-1] = prices[n-1];
        for(int  i=n-2; i>=0; i--)
        {
            max_elem[i] = max(max_elem[i+1], prices[i]);
        }
        
        int max_profit = 0;
        for(int i=0 ;i<n; i++)
        {
            max_profit = max(max_profit, max_elem[i]- prices[i]);
        }
     return max_profit;
    }
   
};
```

Results:   
![image](https://user-images.githubusercontent.com/64036955/174819017-0911a297-f638-48d4-a19f-ae962359600d.png)


