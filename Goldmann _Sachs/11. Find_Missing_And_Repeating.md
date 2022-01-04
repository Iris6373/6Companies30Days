# Problem

## [11. Find Missing And Repeating](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1/#)


# Solution 

## 1) Bit Manipulation - OPTIMAL

       
      
      
   ### Code : (.cpp)
    
          class Solution{
            public:
                int *findTwoElement(int *arr, int n) {
                    int i, x = 0, right = 0, b1 = 0, b2 = 0;
                    int *ans = new int[2];
                    for (i=0;i<n;i++) x ^= arr[i];
                    for (i=1;i<=n;i++) x ^= i;
                    right = x & ~(x-1);
                    for (i=0;i<n;i++) {
                        if ((right & arr[i]) > 0) b1 ^= arr[i];
                        else b2 ^= arr[i];
                    }
                    for (i=1;i<=n;i++) {
                        if ((right & i) > 0) b1 ^= i;
                        else b2 ^= i;
                    }
                    for (i=0;i<n;i++) {
                        if (arr[i] == b1) { ans[0] = b1; ans[1] = b2; return ans; }
                        else if (arr[i] == b2) { ans[0] = b2; ans[1] = b1; return ans; }
                    }
                    return ans;
                }
            };

 
      Time Complexity  : O(N) 
                         Since we traverse all the elements linearly
      Space Complexity : O(1)
                         Since no extra space is used.
