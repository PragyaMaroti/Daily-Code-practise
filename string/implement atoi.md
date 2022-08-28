[Link]()

## Problem Statement:
Your task  is to implement the function atoi. The function takes a string(str) as argument and converts it to an integer and returns it.

Note: You are not allowed to use inbuilt function.  
   
 Task:
Complete the function atoi() which takes a string as input parameter and returns integer value of it. if the input string is not a numerical string then returns -1.    
Note: Numerical strings are the string where either every character is in between 0-9 or where the first character is '-' and the rest all characters are in between 0-9.  


## Solution: 


```cpp

class Solution{
  public:
    /*You are required to complete this method */
    int atoi(string s) {
        //Your code here
        
    int n = s.size();
    bool neg = false;
    if(s[0]=='-')
    neg = true;
    if(neg && s.size()==1)return -1;
    int ans =0; 
    int mul =1;
    
    for(int i=n-1; i>=0; i--)
    {
        if(s[i]>='0' && s[i]<='9') // an integer only
        {
            int temp;
            switch(s[i]){
                case '0' : temp =0;break;
                 case '1' : temp =1;break;
                  case '2' : temp =2;break;
                   case '3' : temp =3;break;
                    case '4' : temp =4;break;
                     case '5' : temp =5;break;
                      case '6' : temp =6;break;
                       case '7' : temp =7;break;
                        case '8' : temp =8;break;
                         case '9' : temp =9;break;
                         
                
            }
            ans+=mul*temp;
            mul*=10;
        }
        else{
            if(i==0 && s[i]=='-')
            continue;
            else
            return -1;
        }
    }
    if(neg)ans*=-1;
    return ans;
     
    
    
    
    }
};

```



- Results:   

![image](https://user-images.githubusercontent.com/64036955/187059410-5b8620f4-f89c-454d-a623-c6e6a2f2f6e7.png)
![image](https://user-images.githubusercontent.com/64036955/187059413-4b332ca6-d12e-4148-92b9-13ea74b22619.png)


