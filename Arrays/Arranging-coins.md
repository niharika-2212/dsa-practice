# Problem: Arranging coins
- Platform: Leetcode 441
- Link: https://leetcode.com/problems/arranging-coins/description
- Difficulty: Easy
- Tags: Math, Binary search

## Problem Statement
You have n coins and you want to build a staircase with these coins. The staircase consists of k rows where the ith row has exactly i coins. The last row of the staircase may be incomplete.

Given the integer n, return the number of complete rows of the staircase you will build.

## Example
```
Input: n = 5
Output: 2
Explanation: Because the 3rd row is incomplete, we return 2.
```

## Approach 1
- Mathematical approach
- total coins used for perfect stairs is step*(step+1)/2
- this value should be less than n 
- rearranging gives us quadratic : `step^2 + step-2n <= 0`
- finding zero of this equation that gives positive value
- `step = (-1+sqrt(1+8*n))/2`
- since values can be big long long is used

### Time complexity
- Time: `O(1)`
- Space: `O(1)` 

### Code (C++)
```c++
int arrangeCoins(int n) {
  long long val = sqrt(1+8LL*n);
  int count = (val-1) / 2;
  return static_cast<int>(count); // converts all values to integers
}
```

## Approach 2 
- using Binary search
- we need to find `step*(step+1)/2<=n`
- consider 1 - n array search using binary search

### Time complexity
- Time: O(logn)
- Space O(1)

### Code (C++)
```c++
int arrangeCoins(int n) {
  long long left = 0;
  long long right = n; // Max possible rows can't exceed n

  long long ans = 0;
  while (left <= right) {
    long long mid = left + (right - left) / 2;
    long long coinsNeeded = mid * (mid + 1) / 2;

    if (coinsNeeded <= n) {
      ans = mid; // This 'mid' is a potential answer, try for more rows
      left = mid + 1;
    } else {
      right = mid - 1; // Too many coins needed, reduce rows
    }
  }
  return static_cast<int>(ans); // converts value to integer
}
```

