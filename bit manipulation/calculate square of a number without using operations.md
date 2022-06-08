[Link](https://www.geeksforgeeks.org/calculate-square-of-a-number-without-using-and-pow/#:~:text=Given%20an%20integer%20n%2C%20calculate,*%2C%20%2F%20and%20pow().&text=A%20Simple%20Solution%20is%20to%20repeatedly%20add%20n%20to%20result.)
### Idea: 

```
If n is even, it can be written as
  n = 2*x 
  n2 = (2*x)2 = 4*x2
If n is odd, it can be written as 
  n = 2*x + 1
  n2 = (2*x + 1)2 = 4*x2 + 4*x + 1
  ```
  
  ### Implementation: 
  
  ```cpp
  // Square of a number using bitwise operators
#include <bits/stdc++.h>
using namespace std;

int square(int n)
{
	// Base case
	if (n == 0)
		return 0;

	// Handle negative number
	if (n < 0)
		n = -n;

	// Get floor(n/2) using right shift
	int x = n >> 1;

	// If n is odd
	if (n & 1)
		return ((square(x) << 2) + (x << 2) + 1);
	else // If n is even
		return (square(x) << 2);
}

// Driver Code
int main()
{
	// Function calls
	for (int n = 1; n <= 5; n++)
		cout << "n = " << n << ", n^2 = " << square(n)
			<< endl;
	return 0;
}
```
