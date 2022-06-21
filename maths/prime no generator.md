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
![image](https://user-images.githubusercontent.com/64036955/174632660-1643685a-53f2-4d27-a186-d590d3c54fcb.png)



### Faster Solution:  

```cpp
class Solution {
public:
    int countPrimes(int n) {
        // 0,1 - not prime, 2 - not count as we count up to n (exclude n itself)
        if (n < 3) return 0;
        
        // not need to step by even's at all, so half vector size, half steps number
        vector<bool> prime(n/2, true);
        int maxi = sqrt(n);
        
        //lets count all odds as potential primes
        int res = n/2;
        
        // steps by odds only
        for (int i = 3; i <= maxi; i+=2) {
            if (prime[i/2]) {
                for(int j = i*i; j < n; j += i*2) {
                    if (prime[j/2]) {
                        // found another not prime
                        prime[j/2] = false;
                        --res;
                    }
                }
            }
        }
        
        // all others are primes
        return res;
    }
};
```
- Results: 


