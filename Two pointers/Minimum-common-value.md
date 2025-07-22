# Problem: Minimum Common Value

- Platform: Leetcode 2540
- Link: https://leetcode.com/problems/minimum-common-value/description
- Difficulty: Easy
- Tags: array, hash table, two pointers, binary search

## Problem Statement
Given two integer arrays nums1 and nums2, sorted in non-decreasing order, return the minimum integer common to both arrays. If there is no common integer amongst nums1 and nums2, return -1.

Note that an integer is said to be common to nums1 and nums2 if both arrays have at least one occurrence of that integer.


## Example

```
Input: nums1 = [1,2,3], nums2 = [2,4]
Output: 2
Explanation: The smallest element common to both arrays is 2, so we return 2.
```

## Approach 
- place two pointers at start of both array
- if values equal return that value
- if not move the smaller pointer forward


### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
int getCommon(vector<int>& nums1, vector<int>& nums2) {
    int i=0,j=0;
    int min=-1;
    int count=0;
    while(i<nums1.size() && j<nums2.size()){
        if(nums1[i]==nums2[j]){
            min=nums1[i];
            break;
            i++;
            j++;
        }else if(nums1[i]<nums2[j]){
            i++;
        }else{
            j++;
        }
    }
    return min;
}
```
