 [link](https://leetcode.com/problems/sort-an-array/)
 
 ## Problem statement:
 Given an array of integers nums, sort the array in ascending order.

 

Example 1:

Input: nums = [5,2,3,1]
Output: [1,2,3,5]
Example 2:

Input: nums = [5,1,1,2,0,0]
Output: [0,0,1,1,2,5]
 

- Constraints:

1 <= nums.length <= 5 * 10^4   
-5 * 10^4 <= nums[i] <= 5 * 10^4   


### Approach 0: STL function

```cpp
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        return nums;
        
    }
};
```
- Results:

![image](https://user-images.githubusercontent.com/64036955/170823781-6a8f0ca2-e8fe-49dc-9c44-ec0f6285eff1.png)


### Approach 1: Bubble sort
```cpp
class Solution {
public:
    vector<int> sortArray(vector<int>& a) {
        int n = a.size();
        for(int i=0; i<n; i++)
        {
            for(int j=0; j<n-i-1; j++)
            {
                if(a[j]>a[j+1]){
                    // swap
                    int temp = a[j];
                    a[j]= a[j+1];
                    a[j+1] = temp;
                }
            }
        }
        return a;
    }
};
```
- **Results: ** 
![image](https://user-images.githubusercontent.com/64036955/170823525-be03371c-1e00-4731-928b-58e793c11318.png)


### Approach 2:  Insertion sort: 

```cpp
class Solution {
public:
    vector<int> sortArray(vector<int>& a) {
        int n = a.size();
        // trying insertion sort
        int i, j, x;
        for(i=1; i<n;i++)
        {
            j=i-1;
            x= a[i];
            while(j>=0 && a[j]>x)
            {
                a[j+1]=a[j];
                j--;
            }
            a[j+1]=x;
        }
        return a;
    }
};

```

- Results: 
![image](https://user-images.githubusercontent.com/64036955/170823594-67243db6-4621-4451-adb8-6ed08acab0be.png)

### Merge sort:  

```cpp
class Solution {
public:
void merge(vector<int>& nums,int s,int e)
        {
		
		 int m=(s+e)/2;  // mid
		 
                int i=s; //starting index
				int j=m+1; 
	
                vector<int>temp;  //extra space
                
              while(i <=m && j<=e )
                 {
                        if (nums[i] < nums[j] )
                        {
                          temp.push_back(nums[i++]);                 
                        }
                       else
                        {
                        temp.push_back(nums[j++]);  
                        }
                }
				
                      while( i<=m )
                      {
                              temp.push_back(nums[i++]);                    
                      }
					  
                      while(j<=e)
                      {
                         temp.push_back(nums[j++]);                          
                      }    
					  
                    int k=0;
                   for(int idx=s;idx<=e;idx++)
                   {
                     nums[idx]=temp[k++];  //copying back all the elements
              }           
                  return; 
            }

        void mergesort(vector<int>& nums,int s,int e)
        {
        if(s>=e)
        {
                return;
        }
                int mid=(s+e)/2;
                mergesort(nums,s,mid); //sort left part
                mergesort(nums,mid+1,e); //sort right part
                
                 return merge(nums,s,e);  //merge both sorted parts
                
        }
    vector<int> sortArray(vector<int>& nums) {
            int s=0;
            int e=nums.size()-1;
            
       mergesort(nums,s,e);
            return nums;
            
    }
};

```
- Results:   

![image](https://user-images.githubusercontent.com/64036955/170823640-b091ea9a-e53b-4bbe-a7d9-3fd3bad8dd1b.png)



### Approach 4: radix sort

```cpp

class Solution {
public:
    void countingsort(vector<int>&A,int k)
    {
        vector<vector<int>>B(10,vector<int>());
        int ten = pow(10,k);
        int n = A.size();
        for(int i = 0; i < n; i++)
        {
            int index = (A[i] / ten) % 10;
            B[index].push_back(A[i]);
        }
        int c = 0;
        for(int i = 0; i < 10; i++)
        {
            for(int j = 0; j < B[i].size(); j++)
            {
                A[c++] = B[i][j];
            }
        }
       
    }
    vector<int> sortArray(vector<int>& nums) {
        int n = nums.size();
        vector<int>P;
        vector<int>N;
        for(int i = 0; i < n; i++)
        {
            if(nums[i] < 0)
            {
                N.push_back( abs(nums[i]) );
            }
            else
            {
                P.push_back(nums[i]);
            }
        }
		// sort the positive numbers
        for(int k = 0; k <= 4; k++)
        {
            countingsort(P,k);
        }
		//sort the negative numbers
        for(int k = 0; k <= 4; k++)
        {
            countingsort(N,k);
        }
		//reverse the result for the negative numbers
        reverse(N.begin(),N.end());
        //convert the numbers into negative
        for(int i = 0; i < N.size(); i++)
            N[i] *= -1;
		// then just append the positive number which were sorted separately
        N.insert(N.end(), P.begin(), P.end());
        return N;
        
        
        
    }
};
```

- Results:  
![image](https://user-images.githubusercontent.com/64036955/170823681-250921e9-9701-4e3b-9c7c-a2fef5d1f00e.png)


