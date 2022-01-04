# Problem

## [13. Decode the string](https://practice.geeksforgeeks.org/problems/decode-the-string2444/1)


# Solution 

## 1) Using String and Frequency Stack - OPTIMAL

      
   ### Code : (.cpp)
    
               class Solution {
                  public:
                      string decodeString(string s) {
                          stack<string> str;
                          stack<int> freq;
                          string curr = "";
                          int i, n = s.size(), no = 0;
                          for (i=0;i<n;i++) {
                              if (s[i] >= '0' && s[i] <= '9') no = no*10 + (s[i]-'0');
                              else if (s[i] >= 'a' && s[i] <= 'z') curr += s[i];
                              else if (s[i] == '[') {
                                  str.push(curr);
                                  freq.push(no);
                                  no = 0;
                                  curr = "";
                              }
                              else {
                                  string x = str.top(); str.pop();
                                  int y = freq.top(); freq.pop();
                                  while (y--) x += curr;
                                  curr = x;
                              }
                          }
                          return curr;
                      }
                  };

 
      Time Complexity  : O(N) 
                         Since we traverse through the string
      Space Complexity : O(N)
                         Since the maximum size of stack can be N
