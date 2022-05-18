![image](https://user-images.githubusercontent.com/64036955/169029127-211e9dd7-52b8-4d95-8b38-804a5db5ed4c.png)



1. To check if a number is odd or even:

        If x & 1 = 0 then x is even 
        If x & 1 = 1 then x is odd.
        x is divisible by 2^k exactly when x & (2^k – 1) = 0.
        
2. Multiplication: right shift operation for multiplication with 2^1, to multiply with 2^k, right shift by k.
          
          x>>k

3. Division: left shift operation, to divide with 2^k, left shift by k.
          
          x<<k
          
4. To check the index of set(1) bits in a number(0-indexed number). 
        
        void printing_subset(int subset){
        for (int i = 0; i < 32; i++) 
	    {
		    if (subset & (1 << i)) std::cout << i << " ";
	    }
      }
      
      
      the condition:
      
        (1 << i)
        
     this is used to check every index's bit (since 1 is represented in 32 bit integer, when right shifted, it becomes: 2,4,8 and so on, basically in binary representation, it shifts the position evevry time).
     
     
5. To form subsets and add element to it.   


              int add_elements_to_subset()
          {
        int subset = 0;
        subset = subset | (1 << 1);
        subset = subset | (1 << 3);
         subset = subset | (1 << 4);
        subset = subset | (1 << 8);
        return subset;
        }

