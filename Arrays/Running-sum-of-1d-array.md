# Problem: Running Sum of 1d Array

- Platform: Leetcode 1480
- Link: https://leetcode.com/problems/running-sum-of-1d-array/description/
- Difficulty: easy
- Tags: Array, prefix sum

## Problem Statement
Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`.

Return the running sum of `nums`.

## Example
```
Input: nums = [1,2,3,4]
Output: [1,3,6,10]
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```

## Approach 
- create an array for prefix sum
- initialise a variable sum =0 (stores cumulative sum at each step)
- traverse in `nums`. For each element add it to sum and push in final array

### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
vector<int> runningSum(vector<int>& nums) {
    vector<int>final(nums.size());
    int sum=0;
    for(int i=0 ; i<nums.size() ; i++){
        sum+=nums[i];
        final[i] = sum;
    }
    return final;
}
```
