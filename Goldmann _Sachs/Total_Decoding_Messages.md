# Problem

## [Total Decoding Messages](https://practice.geeksforgeeks.org/problems/total-decoding-messages1235/1/)


# Solution 

## 1) Bottom Up DP - BETTER

       
      
      
   ### Code : (.cpp)
    
          class Solution {
          public:
              int dfs(string s, int i, int n, int mod, vector<int>& dp) {
                  if (i == n) return 1;
                  if (dp[i] != -1) return dp[i];
                  int a = 0, b = 0, c = 0;
                  if (s[i] >= '1' && s[i] <= '9') a = dfs(s, i+1, n, mod, dp);
                  else return 0;
                  if (i+1 < n) {
                      int no = stoi(s.substr(i,2));
                      if (no <= 26) b = dfs(s, i+2, n, mod, dp);
                  }
                  return dp[i] = (a+b) % mod;
              }

            int CountWays(string s){
                int i, j, n = s.size(), mod = 1e9+7;
                if (n == 0) return 1;
                else if (s[0] == '0') return 0;
                else if (s.size() == 1) return 1;
                else if (s.substr(n-2,2) == "00") return 0;
                for (i=0;i<n-1;i++) if (s.substr(i,2) == "00") return 0;

                vector<int> dp(n,-1);
                return dfs(s, 0, n, mod, dp);
            }

        };

 
      Time Complexity  : O(N) 
                         Since we traverse all the characters once
      Space Complexity : O(N)
                         Since we use a map to store extra space.
