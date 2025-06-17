# Problem: Two Sum
- Platform: LeetCode
- Link: https://leetcode.com/problems/two-sum/
- Difficulty: Easy
- Tags: Array, Hash Table

## Problem Statement
> Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

## Approach
- Use a hash map to store the difference between `target` and current element.
- Check if current element exists in the map.

## Time Complexity
- Time: O(n)
- Space: O(n)

## Code (Python)
```python
def twoSum(nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in hashmap:
            return [hashmap[diff], i]
        hashmap[num] = i
```

## Output
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
```
