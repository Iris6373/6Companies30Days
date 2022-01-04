# Problem

## [15_Array Pair Sum Divisibility Problem ](https://practice.geeksforgeeks.org/problems/array-pair-sum-divisibility-problem3257/1#)


# Solution 

## 1) Storing remainders in Hash Table - OPTIMAL

       
      
      
   ### Code : (.cpp)
    
          class Solution {
            public:
              bool canPair(vector<int> nums, int k) {
                  int i, j, n = nums.size(), ans = 0,x,y;
                  map<int,int> mp;
                  for (i=0;i<n;i++) mp[nums[i]%k]++;
                  i = 1, j = k-1;
                  while (i <= j) if (mp[i++] != mp[j--]) return 0;
                  return mp[0]%2 == 0;
              } 
          };

 
      Time Complexity  : O(N) 
                         Since we traverse all the elements once
      Space Complexity : O(K)
                         Since the maximum map size can be remainders of nums[i]%K
