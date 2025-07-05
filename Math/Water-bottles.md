# Problem: Water Bottles

- Platform: Leetcode 1518
- Link: https://leetcode.com/problems/water-bottles/description
- Difficulty: Easy
- Tags: Math

## Problem Statement
There are numBottles water bottles that are initially full of water. You can exchange numExchange empty water bottles from the market with one full water bottle.

The operation of drinking a full water bottle turns it into an empty bottle.

Given the two integers numBottles and numExchange, return the maximum number of water bottles you can drink.


## Example

```
Input: numBottles = 9, numExchange = 3
Output: 13
Explanation: You can exchange 3 empty bottles to get 1 full water bottle.
9- 3 +1 = 7- 3 +1 = 5- 3 +1 = 3- 3 +1 = 1  
Number of water bottles you can drink: 3 + 3 + 3 + 3 + 1 = 13.
```

## Approach 1
- repeat till numBottles>=numExchange
- if yes exchange bottles for 1 (`numBottles-numExchange+1`)

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
int numWaterBottles(int numBottles, int numExchange) {
    int count=0;
    while(numBottles>=numExchange){
        count+=numExchange;
        numBottles = numBottles-numExchange+1;
    }
    count+=numBottles;
    return count;
}
```
