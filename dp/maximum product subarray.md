[Link](https://leetcode.com/problems/maximum-product-subarray)


### Problem Statement:  



### Approach: Brute-force:  

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        int max_product =INT_MIN;
       // trying brute force
        for(int i=0; i<n; i++) // starting index
        {   int product_from_here =1;
            for(int j=i; j<n; j++) // increasing the sizes
            {
                product_from_here *=nums[j];
                max_product = max(max_product, product_from_here);
            }
        }
        return max_product;
    }
};
```

![image](https://user-images.githubusercontent.com/64036955/177924783-44dd4a7b-a65b-423c-9cb5-7fbc239ea860.png)
   
   ⏰O(n^2)
   
### If there were no zeroes in the array:   

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        int max_product =INT_MIN;
       // trying brute force
// trying to make a contiguous product array and finding in between negetives.   
        
        vector<int>cont_prod(n);
        cont_prod[0]= nums[0];
        for(int i=1;i<n; i++)
            cont_prod[i] = nums[i]*cont_prod[i-1];
        //nums = [2,3,-2,4]
        // cont_prod = [2,6,-12,-24]
        int first_neg =-1; int second_neg =-1;
        int i=0;
        int max_prod = cont_prod[0];
        while(i<n)
        {   max_prod = max(max_prod, cont_prod[i]);
            if(cont_prod[i] <0)
            {
                first_neg = i;
                while(i<n&& cont_prod[i]<0)
                    i++;
                second_neg = i-1; // even if it is n, it works;
                int temp = cont_prod[second_neg]/ cont_prod[first_neg];
                max_prod = max(temp, max_prod);
            }
         else i++;
        }
        return max_prod;
        }
        // un
    
    
    
    
    
};

```

### For the generic integer case:  


``` cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        int max_product =INT_MIN;
       // trying brute force
// trying to make a contiguous product array and finding in between negetives.   
        
        vector<int>cont_prod(n);
        cont_prod[0]= nums[0];
        cout<<cont_prod[0]<<" ";
        for(int i=1;i<n; i++)
        {
             if(cont_prod[i-1]==0) cont_prod[i] = nums[i];
           else cont_prod[i] = nums[i]*cont_prod[i-1];
            cout<< cont_prod[i]<<" ";
        }
        //if(cont_prod[n-1]>0)return cont_prod[n-1]; : not gonna work in cases of zeroes
        //nums = [2,3,-2,4]
        // cont_prod = [2,6,-12,-24]
        int first_neg =-1; int second_neg =-1;
        int i=0;
        int max_prod = cont_prod[0];
        while(i<n)
        {   max_prod = max(max_prod, cont_prod[i]);
         if(cont_prod[i]==0)
         {
             first_neg =-1; second_neg =-1;
         }
            if(cont_prod[i] <0)
            {
                if(first_neg==-1)first_neg = i;
                while(i<n&& cont_prod[i]<0)
                    i++;
                second_neg = --i; // even if it is n, it works;
                if(first_neg!= second_neg){int temp = cont_prod[second_neg]/ cont_prod[first_neg]; max_prod = max(temp, max_prod);}
            }
                
                
         i++;
        }
        return max_prod;
        }
        // un
    
    
    
    
    
};

```

- Results:  

![image](https://user-images.githubusercontent.com/64036955/177932734-22501550-2ac3-4d46-a5eb-7eddd5e3bfea.png)


