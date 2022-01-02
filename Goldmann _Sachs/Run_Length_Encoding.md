# Problem

## [Run Length Encoding](https://practice.geeksforgeeks.org/problems/run-length-encoding/1/#)


# Solution 

## 1) One Pass - OPTIMAL

       Simulation
      
      
   ### Code : (.cpp)
    
          string encode(string src)
          {     
            int i, n = src.size(), a = 1;
            string ans = "";
            char ch = src[0];
            for (i=1;i<n;i++) {
                if (ch == src[i]) a++;
                else {
                    ans += ch;
                    ans += to_string(a);
                    a = 1;
                    ch = src[i];
                }
            }
            ans += ch;
            ans += to_string(a);
            return ans;
          } 

 
      Time Complexity  : O(N) 
                         Since we traverse all the chars once
      Space Complexity : O(1)
                         Since no extra space is used.
