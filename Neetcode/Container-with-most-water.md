# Problem: Container with most water

- Platform: Neetcode
- Link: https://neetcode.io/problems/max-water-container?list=neetcode150
- Difficulty: Medium
- Tags: Two pointers

## Problem Statement
You are given an integer array heights where heights[i] represents the height of the ith bar.

You may choose any two bars to form a container. Return the maximum amount of water a container can store.


## Example

```
Input: height = [1,7,2,5,4,7,3,6]

Output: 36
```

## Approach 1
- place two pointer at start and end
- the distance between two pointers is width
- and min of the heights at those pointers is height
- save the volume (area in this case distance*minofheights) in a variable
- move the smaller pointer ahead
- calculate again
- return the maximum value

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
int maxArea(vector<int>& heights) {
    int i=0 ;
    int j=heights.size()-1;
    int maxwater=0;
    while(i<=j){
        int diff = j-i;
        int min=0;
        if(heights[i]<heights[j]){
            min=heights[i];
        }else{
            min=heights[j];
        }
        if(min*diff>maxwater){
            maxwater=min*diff;
        }
        if(heights[i]<heights[j]){
            i++;
        }else{
            j--;
        }
    }
    return maxwater;
}
```
