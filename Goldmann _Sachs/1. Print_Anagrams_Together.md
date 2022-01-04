# Problem Statement

## [Print Anagrams Together](https://practice.geeksforgeeks.org/problems/print-anagrams-together/1/#)


## 1) Hash Table - BRUTE FORCE

     We store groups of anagrams in a map using the number of characters as key.
  
        
   ### Code : (.cpp)  
      
          class Solution{
          public:
            vector<vector<string> > Anagrams(vector<string>& sl) {
                map<vector<int>,vector<string>> mp;
                vector<vector<string>> ans;
                int i, a = 1;
                for (string s : sl) {
                    vector<int> v(26,0);
                    for (char ch : s) v[ch-'a']++;
                    mp[v].push_back(s);
                }
                for (auto it=mp.begin(); it!=mp.end(); it++) {
                    vector<string> y = it->second;
                    vector<string> v;
                    for (i=0;i<y.size();i++) v.push_back(y[i]);
                    ans.push_back(v);
                }
                return ans;
            }
        };


    Time Complexity  : O(N*M)
                       Since we visit all strings twice.

    Space Complexity : O(N*M)
                       Since a map is used to store all strings according to its key.
