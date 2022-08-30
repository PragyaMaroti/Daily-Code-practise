
### Problem Statement:  

Yogi and Dharam, who are chefs in EatClub, are playing a game in which one has to solve the problem in order to get out of the outlet for a short break. Dharam goes first and Yogi gives him a problem. Dharam needs your help to solve the problem.

Given a range from A to B, your task is to count the numbers in which the difference between adjacent digits is not more than one.

Note : In case of single digit, assume the difference to be 0.

```
Input Format:

The first line of input contains a single integer T.   

The next T lines contain two space separated integers each containing values of A and B.    

Constraints:

1 <= T <= 100   
1 <= A, B <= 10^12   
Output Format:   

For each test case print the count of numbers in the range [A, B] in a new line.

Sample Input 0

2
10 30
1 10
Sample Output 0

6
10
Explanation 0

10, 11, 12, 21, 22, 23
1, 2, 3, 4, 5, 6, 7, 8, 9, 10

```


### Solution:  

```cpp

#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
#include<bits/stdc++.h>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */   
   
    
    int t ;
    cin>>t;
    for(int i=0; i<t; i++)
    {   
        int count =0;
        int mini , maxi;
        cin>>mini>>maxi;
       // if(maxi<=12)
        //{
          //  cout<<maxi - mini + 1;
           // return 0;
        //}
        // for every 11 numbers there are 3 such numbers;
        //int l, r;
        //if(mini <11)
         // count+= 11-mini+1;
        //l = mini/11;
        //if(l<1)l=1;
        //r = maxi/11;
        int count =0;
        int i=mini;
        while(i<=maxi)
        {
            if(i<11){i++ count++;}
            if(i%11==0 && i+11<=maxi)
            {  
            count+=3;
                i+=11;
             
            }
             else{
                 int a = i/11, b = i%11;
                 if(a-b ==1 || a-b ==0 || a-b ==1)count++;
                 i++;
             }
             
            }
        cout<<count<<endl;
        }
        
        
        
    
    
    return 0;
}
```
