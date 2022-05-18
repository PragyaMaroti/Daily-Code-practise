- [Link](https://practice.geeksforgeeks.org/problems/count-total-set-bits-1587115620/1#)
- **Problem**: 
You are given a number N. Find the total count of set bits for all numbers from 1 to N(both inclusive).
Expected Time Complexity: **O(log N).**
Expected Auxiliary Space: O(1).

- **Constraints:**
1 ≤ N ≤ 10^8

- Basic way of counting the set bits: 
```cpp
int count =0;
for(int i=0; i<32; i++)
{   if(number & (1<<i)) count++;
}


```
If we use this, the time complexity would be proportional to O(N) in this problem.   

We can observe a pattern below:   
let n=11, then :
![image](https://user-images.githubusercontent.com/64036955/169027671-c4807f08-8375-4714-b8dd-83d9e03c9339.png)   
till 7(111) we have a fixed number of total numbers of 1, which goes for every 2^k -1 as the limit to count.  
It uses simple observation or P&C to say that it would be equal to:
          
          ((2^k)*k)/2

Now, the remainig bits is counted as shown below:   
![image](https://user-images.githubusercontent.com/64036955/169028258-c8f93713-8d49-4a3f-ac55-914ee312b829.png)   
here, we get another subproblem, hence it becomes recursive.  


- Code:  

```cpp
class Solution{
    public:
    // n: input to count the number of set bits
    //Function to return sum of count of set bits in the integers from 1 to n.
    int highest_power(int n)
    {
        int p =0;
        while(pow(2, p)<=n)
        p++;
        return p-1;
    }
    int countSetBits(int n)
    {   if(n<=1) return n;
            
        // find k, the highrst power of 2 wiz less than n.
        int k = highest_power(n);
        int boundary = pow(2,k);
        return k*pow(2,k)/2 + n- boundary+1 + countSetBits(n-boundary);    }
};
```

![image](https://user-images.githubusercontent.com/64036955/169028587-1d3e1f59-13ed-43d0-a21e-7a2fc6024187.png)
