question link: [2 sum](https://leetcode.com/problems/two-sum/)
approaches:
1. Brute-force:
```cpp
int n = nums.size();
        for(int i=0; i<n; i++)
        {
          int temp = target - nums[i];
            for(int j=i+1; j<n;j++)
            {
                if(nums[j]== temp)
                {
                    ans[0] = i;
                    ans[1]= j;
                    return ans; 
                }
            }
          
```
- Comments: 
time complexity: O(n^2)
space complexity : O(1) // constant additinoal space requirement.
```cpp
 vector<int> ans;
        unordered_map<int, int> numMap;
        
        // target = 6
        // 3        2        4 
        //(3, 0)   (2, 1)   
        // i = 0   i = 1    i = 2
        
        // (condition satisfied at i = 2) as 6 - 4 i.e. 2, is present in map,
        // so return index where 2 was found (i = 1) and return current index (i = 2).
        
        for(int i = 0; i < nums.size(); i++) {
            if(numMap.find(target - nums[i]) != numMap.end()) {
                ans.push_back(numMap[target - nums[i]]);
                ans.push_back(i);
                return ans;
            }
            numMap[nums[i]] = i;
        }
        return ans;
    }
```
- Comments:
time complexity: O(n)
space complexity: O(n) // dependent on the size of the vector nums, map size will vary.

3. Binary search
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> duplicate,ans;
        duplicate=nums;
        int len=nums.size();
        int low(0),high(len-1);
        sort(nums.begin(),nums.end());
        while(low<high){
            int sum(nums[low]+nums[high]);
            if(target==sum) break;
            else if(target>sum) low++;
            else if(sum > target) high--;
        }
        
        for(int i=0;i<len;i++){
            if(nums[low]==duplicate[i]) ans.push_back(i);
            else if (nums[high]==duplicate[i]) ans.push_back(i);
        }
        return ans;
    }
};
```
- Comments: 

time complexity: O(n) +O(logn) = O(n)
space complexity: O(n)


NOTE: approach 3 is fastest. 




