[Problem's Link](https://practice.geeksforgeeks.org/problems/validate-an-ip-address-1587115621/1)


### Solution:  
```cpp
class Solution {
    public:
        int isValid(string s) {
            
            int n = s.size();
            if(n>15) // max size possible
            return 0;
            int dotCount=0;
            string temp = "";       
           // cout<<"1"<<endl;
     
            for(int i=0; i<n; i++)
            {  // cout<<temp<<endl;

                if(s[i]=='.')
                {   dotCount++;
                    // . is found, check its previous values formed yet
                  // int value =0;
                    //int mul = 1;
                   // int m = temp.size();
                    //if(m>3)return false;
                    //for(int j=m-1; j>=0; j++)
                    //{
                      //  value += int(s[j]-'0') *mul;
                    //    mul*=10;
                    //}
                   // if(value>256)return 0;
                if(temp.size()<1 || temp.size()>3)return 0;
                int value = stoi(temp);
                if(value<10 && temp.size()>1)return 0;
                if(value<100 && temp.size()>2)return 0;
                
                if(value>=256)return 0;
                    // reset the temp
                    temp = "";
                }
                else
                {   if(s[i]>='0' && s[i]<='9')
                    temp += s[i];
                    else
                    return 0;
                }
            }
            // check temp for the last time;
             if(temp.size()<1 || temp.size()>3)return 0;
                int value = stoi(temp);
                if(value<10 && temp.size()>1)return 0;
                if(value<100 && temp.size()>2)return 0;
                
                if(value>=256)return 0;
                    if(dotCount<3 || dotCount>3)return 0;
                    return 1;
                    
        }
};
```


### Results: 

![image](https://user-images.githubusercontent.com/64036955/187031111-68e67603-e3f1-47f3-98e5-984f73e743e8.png)
