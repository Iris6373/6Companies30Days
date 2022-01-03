# Problem Statement

## [3. Count the subarrays having product less than k](https://practice.geeksforgeeks.org/problems/count-the-subarrays-having-product-less-than-k1708/1/#)


## 1) Sliding Window - OPTIMAL

     
  
        
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
