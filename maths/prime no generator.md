[Leetcode Link](https://leetcode.com/problems/count-primes/)

### Problem Statement: 
Given an integer n, return the number of prime numbers that are strictly less than n.   
- Constraint:

0 <= n <= 5 * 10^6

### Solution:  

**Prime Number Sieves**
[reference video](https://www.youtube.com/watch?v=Xxu95iiVcPI&list=PLMCXHnjXnTnuX59JRYLwyr6IFkuqTr0oa&index=4)


```cpp
class Solution {
public:
    int countPrimes(int n) {
         if(n<=2)return 0;
       vector<int> hash(n, 1) ;
        hash[0]=-1; hash[1]=-1;
       
        
        int count =0;
        for(int i=2; i<sqrt(n); i++)
        {   if(hash[i]!=-1)
        {  
            int mul =2;
            while(mul*i<n)
            { hash[mul*i]=-1; mul++;}
        }
        
        }
        for(int i=2; i<n; i++)
            if(hash[i]!=-1)count++;
        return count;
    }
};
```

- Results:  

