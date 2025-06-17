# Problem: Binary Search
- Platform: Leetcode 704
- Link: https://leetcode.com/problems/binary-search/description/
- Difficulty: Easy
- Tags: Array, Binary search

## Problem Statement
Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its `index`. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

## Output
```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4 // 9 exist at index 4
```

## Approach
- use **Binary search** - dividing the array in half at each step
- find middle of the array
- if target == mid, return index
- if target greater than mid, search in second half
- else search in first half

### time complexity
- Time: `O(logn)`
- Space: `O(1)` (for iterative)

### Code (C++)
```c++
int search(vector<int>& nums, int target) {
        int l = 0;
        int r = nums.size()-1;
        while(r>=l){
            int m = l+(r-l)/2;
            if(nums[m]==target){
                // found
                return m;
            }
            else if(nums[m]<target){
                l=m+1;
            }
            else {
                r=m-1;
            }
        }
        return -1;
    }
```

