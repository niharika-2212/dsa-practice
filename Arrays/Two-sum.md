# Problem: Two sum
- Platform: Leetcode 1
- Link: https://leetcode.com/problems/two-sum/description/
- Difficulty: Easy
- Tags: Array, Binary search, hash table

## Problem Statement
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Example
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

## Approach 1
- naive approach
- use nested loops to generate all pairs and compare to get target

### Time complexity
- Time: `O(n^2)`
- Space: `O(1)` (for iterative)

### Code (C++)
```c++
vector<int> twoSum(vector<int>& nums, int target) {
  vector<int>v;
  int t1,t2;
  for(int i=0 ; i<nums.size() ; i++){
    for(int j=0 ; j<nums.size() ; j++){
      if(target==nums[i]+nums[j] && i!=j){
        t1=i;
        t2=j;
      }
    }
  }
  v.push_back(t1);
  v.push_back(t2);

  return v;
}
```

## Approach 2
- sort and binary search
- Sort the array
- for each element in array calculate `val = target-element`
- binary search in the array again to find val

### Time complexity
- Time: `O(nlogn)`
- Space: `O(1)`

### Code (C++)
```c++
bool binarySearch(vector<int> &arr, int left, int right, int target){
    while (left <= right){
        int mid = left + (right - left) / 2;

        if (arr[mid] == target)
            return true;
        if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return false;
}

// Function to check whether any pair exists
// whose sum is equal to the given target value
bool twoSum(vector<int> &arr, int target){
    
    sort(arr.begin(), arr.end());

    // Iterate through each element in the array
    for (int i = 0; i < arr.size(); i++){
        int complement = target - arr[i];

        // Use binary search to find the complement
        if (binarySearch(arr, i + 1, arr.size() - 1, complement))
            return true;
    }
  
    // If no pair is found
    return false;
}
```

## Approach 3
- use hash set
- create empty hash set
- iterate over the array and find `val = target-element`
- check if val exist in hash set
  - if yes, pair found
  - if no, add element to set
- if loop  completes, pair not found

### Time complexity
- Time: `O(n)` (searching in hashset takes O(1) time)
- Space: `O(n)`

### Code (C++)
```c++
bool twoSum(vector<int> &arr, int target){
  
    // Create an unordered_set to store the elements
    unordered_set<int> s;

    // Iterate through each element in the vector
    for (int i = 0; i < arr.size(); i++){

        // Calculate the complement that added to
        // arr[i], equals the target
        int complement = target - arr[i];

        // Check if the complement exists in the set
        if (s.find(complement) != s.end())
            return true;

        // Add the current element to the set
        s.insert(arr[i]);
    }
  
    // If no pair is found
    return false;
}
```