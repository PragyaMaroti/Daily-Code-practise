 [link](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1#)

## Problem Statement: 
Given an unsorted array Arr of size N of positive integers. One number 'A' from set {1, 2, …N} is missing and one number 'B' occurs twice in array. Find these two numbers.
Complete the function findTwoElement() which takes the array of integers arr and n as parameters and returns an array of integers of size 2 denoting the answer ( The first index contains B and second index contains A.)

- Expected Time Complexity: O(N)
- Expected Auxiliary Space: O(1)

- Constraints:
1 ≤ N ≤ 105
1 ≤ Arr[i] ≤ N


### Approach 1: Using hash array:
 
 ```cpp
// { Driver Code Starts
#include <bits/stdc++.h>

using namespace std;

 // } Driver Code Ends
class Solution{
public:
    int *findTwoElement(int *arr, int n) {
        vector<int>array(n+1, 0);
       // for(int i=0; i<n; i++)cout<<array[i]<<" ";
         int ans[2];
        //int*p =&ans[0];
        for(int i=0; i<n; i++)
        {   int temp = *arr;
            //cout<<temp<<endl;
            array[temp]++;
            //cout<<array[temp]<<endl;
            arr++;
        }
        for(int i=1; i<=n; i++)
        {
            if(array[i]==2)ans[0]=i;
            if(array[i]==0)ans[1]=i;
        }
        int*p = ans;
        return p;
        
        ;
    }
};

// { Driver Code Starts.

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        int a[n];
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }
        Solution ob;
        auto ans = ob.findTwoElement(a, n);
        cout << ans[0] << " " << ans[1] << "\n";
    }
    return 0;
}  // } Driver Code Ends

```

Time complexity: O(N)   
Space Complexity: O(N)

### Approach 2: Marking the visited elements as indices
Traverse the array. While traversing, use the absolute value of every element as an index and make the value at this index as negative to mark it visited. If something is already marked negative then this is the repeating element. To find missing, traverse the array again and look for a positive value.
```cpp
#include <bits/stdc++.h>
using namespace std;

void printTwoElements(int arr[], int size)
{
    int i;
    cout << "The repeating element is ";

    for (i = 0; i < size; i++) {
        if (arr[abs(arr[i]) - 1] > 0)
            arr[abs(arr[i]) - 1] = -arr[abs(arr[i]) - 1];

        else
            cout << abs(arr[i]) << "\n";
    }

    cout << "and the missing element is ";
    for (i = 0; i < size; i++) {
        if (arr[i] > 0)
            cout << (i + 1);
    }
}

/* Driver code */
int main()
{
    int arr[] = { 7, 3, 4, 5, 5, 6, 2 };
    int n = sizeof(arr) / sizeof(arr[0]);
    printTwoElements(arr, n);
}

```

Time complexity: O(N)   
Space Complexity: O(1)
