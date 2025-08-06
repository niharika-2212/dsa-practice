# Problem: Single Number

- Platform: Leetcode 136
- Link: https://leetcode.com/problems/single-number/description/
- Difficulty: Easy
- Tags: array, bit manipulation

## Problem Statement
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.


## Example
```
Input: nums = [2,2,1]
Output: 1
```

## Approach 1
- using two pointers
- place two pointers at 0 and 1 index
- if elements at pointers is equal, move both +2 forward to get new values on both
- if not equal return that value


### Time complexity
- Time: `O(nlogn)` 
- Space: `O(1)`

### Code (C++)
```c++
int singleNumber(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    int final=0;
    int i=0, j=1;
    while(i<=nums.size()-1 && j<=nums.size()-1){
        if(nums[i]!=nums[j]){
            final=nums[i];
            return final;
        }else{
            i=i+2;
            j=j+2;
        }
    }
    if(i<nums.size()){
        return nums[i];
    }
    if(j<nums.size()){
        return nums[j];
    }

    return final;
}
```

## Approach 2
- using XOR
- property of xor
    - xor with same number is 0
    - xor of 0 with different number is the number itself
- initialise result=0
- for each element in array calculate xor with result
- each repeated value will be canceled out
- at the end we will be left with non-repeated value
- ex. 
    - [1,2,2,1,3]
    - res=0
    - i=0 -> res=1
    - i=1 -> res=3
    - i=2 -> res=1
    - i=3 -> res=0
    - i=4 -> res=3
    - return 3

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
int singleNumber(vector<int>& nums){
    int res=0;
    for(int i=0 ; i<nums.size() ; i++){
        res ^= nums[i];
    }
    return res;
}
```