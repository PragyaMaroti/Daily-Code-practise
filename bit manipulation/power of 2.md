[Link](https://bit.ly/31geZzE)


### Solution:  

```cpp
bool isPowerOfTwo(int n)
{ // a power of 2 will have only one 1 in it's bit representaion.
  
    int count =0;
    for(int i=0; i<32; i++)
    {    if(count>1)return false;  // can't be a power of 2
        if((1<<i & n)>0)count++; // if the ith bit is 0 in n, then this will be zero only.
    }
  
    return true; // as there's numbers above 0 only.
}
```

### A better approach:  

If we subtract a power of 2 numbers by 1 then all unset bits after the only set bit become set; and the set bit becomes unset.

 

For example for 4 (100) and 16 (10000), we get the following after subtracting 1

3 -> 011

15 -> 01111

So, if a number ‘N’ is power of 2 then bitwise & of ‘N’ and ‘N’-1 will be zero. We can say ‘N’ is a power of 2 or not based on the value of ‘N’&('N'-1). The expression ‘N’&('N'-1) will not work when ‘N’ is 0. To handle this case also, our expression will become ‘N’&(!'N'&('N'-1)).   

```cpp

bool isPowerOfTwo(int n)
{	
    // First n in the below expression is for the case when n is 0.
    return n != 0 && ((n & (n - 1)) == 0);
}
```


