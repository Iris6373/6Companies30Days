# Problem

## [Overlapping rectangles](https://practice.geeksforgeeks.org/problems/overlapping-rectangles1924/1/#)


# Solution 

## 1) Positive Area - OPTIMAL

       The area of the rectangle formed by 2 rectangles must have positive area.
       For that, we check if any of 4 sides are away from each other.
       (i.e) rect1[right] < rect2[left] or rect1[top] < rect2[bottom] or rect2[left] < rect1[right] or rect2[top] < rect1[bottom]
       If so, we return 0.
       Else 1.
       
      
   ### Code : (.cpp)
    
          class Solution {
          public:
            int doOverlap(int l1[], int r1[], int l2[], int r2[]) {
                if (r1[0] < l2[0] || r2[0] < l1[0] || l1[1] < r2[1] || l2[1] < r1[1]) return 0;
                return 1;
            }
        };

 
      Time Complexity  : O(1) 
                         Since it takes constant time
      Space Complexity : O(1)
                         Since no extra space is used.
