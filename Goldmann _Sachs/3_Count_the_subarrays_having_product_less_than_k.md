# Problem Statement

## [3. Count the subarrays having product less than k](https://practice.geeksforgeeks.org/problems/count-the-subarrays-having-product-less-than-k1708/1/#)


## 1) Sliding Window - OPTIMAL

     We perform the normal sliding window to count all subsets in that window.
     But, there might be a case where, we count same subsets more than once.
     
     For (e.g) 
     10 13
     1 2 2 3 2 1 1 3 1 1
     
     For this test case, the answer is 10(individual elements) + 6(0-3) + 9(2-6) + 12(4-9) = 37
     If we do not subtract the duplicates, we get 10 + 6 + 10(2-3) + 15(4-6).
  
        
   ### Code : (.cpp)  
      
          class Solution{
            public:
              int countSubArrayProductLessThanK(const vector<int>& v, int n, long long k) {
                  long long i, j = 0, prev = -1, prod = v[0], a = 0, ans = 0;
                  if (v[0] < k) ans++;
                  for (i=1;i<n;i++) {
                      if (v[i] < k) ans++;
                      if (prod*v[i] < k) prod *= v[i];
                      else {
                          ans += (i-j)*(i-j-1)/2;
                          if (prev > j) ans -= (prev-j)*(prev-j+1)/2; 
                          prod *= v[i];
                          prev = i-1;
                          while (j < i && prod >= k) prod /= v[j++];
                      }
                  }
                  ans += (i-j)*(i-j-1)/2;
                  if (prev > j) ans -= (prev-j)*(prev-j+1)/2; 
                  return ans;
              }
          };

    Time Complexity  : O(N)
                       Since we traverse all elements once.

    Space Complexity : O(1)
                       Since no extra space is used.
