[Link](https://leetcode.com/problems/sum-of-numbers-with-units-digit-k/)

### Problem Statement: 
Given two integers num and k, consider a set of positive integers with the following properties:

- The units digit of each integer is k.   
- The sum of the integers is num.   
Return the minimum possible size of such a set, or -1 if no such set exists.

Note:

- The set can contain multiple instances of the same integer, and the sum of an empty set is considered 0.   
- The units digit of a number is the rightmost digit of the number.   

```
Example 1:

Input: num = 58, k = 9
Output: 2
Explanation:
One valid set is [9,49], as the sum is 58 and each integer has a units digit of 9.
Another valid set is [19,39].
It can be shown that 2 is the minimum possible size of a valid set.
Example 2:

Input: num = 37, k = 2
Output: -1
Explanation: It is not possible to obtain a sum of 37 using only integers that have a units digit of 2.
Example 3:

Input: num = 0, k = 7
Output: 0
Explanation: The sum of an empty set is considered 0.
```

- Constraints:

1. 0 <= num <= 3000    
2. 0 <= k <= 9   

### Solution: 

💡 Sum of numbers with same one's digit 's one's digit can be pre-determined as the multiplication table of how many numbers we have taken. As these numbers can repeat as well, we start from the lower numbers to get minimum of them.      
💡Therefore, to have a possible combinations of digits to get a sum as target, the one's digit  of target must match with one of the  multiples of 'K'. If such multiple is found, then we can distribute the rest numbers as we wish (multiples of 10).   
👉 Also, Note the condition: temp<=nums: as the minimum sum can be temp.   
Hence, the following code serves the purpose of this question: 


```cpp
class Solution {
public:
    int minimumNumbers(int nums, int k) {
        if(nums==0)return 0;
        if( nums<k)return -1;
       // if(nums==k)return 1;
       
        //if(nums%2 !=0 && k%2==0)return -1;
        for(int i=1; i<=10; i++)
        {
         int temp = k*i;
            if(nums%10 == temp%10 && temp<=nums)
                return i;
        }
        return -1;
    }
};

- Results:   
![image](https://user-images.githubusercontent.com/64036955/174470114-ff7bd105-d365-4226-a321-ed655200d709.png)
   
