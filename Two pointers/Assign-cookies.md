# Problem: Assign cookies

- Platform: Leetcode 455
- Link: https://leetcode.com/problems/assign-cookies/description
- Difficulty: Easy
- Tags: Array, two pointers, greedy, sorting

## Problem Statement

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

## Example

```
Input: g = [1,2,3], s = [1,1]
Output: 1
Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3.
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```

## Approach

- sort the two arrays
- place two pointers at start of both
- check if greed factor is <= cookie size (eat), move both pointer
- if not move just cookie (same person can eat another cookie ahead)

### Time complexity

- Time: `O(n log n + m log m)`
- Space: `O(1)`

### Code (C++)

```c++
int findContentChildren(vector<int>& g, vector<int>& s) {
    sort(s.begin(), s.end());
    sort(g.begin(), g.end());
    int count=0;
    int i=0, j=0;
    while(i<g.size() && j<s.size()){
        if(g[i]<=s[j]){
            count++;
            i++;
            j++;
        }else{
            j++;
        }
    }
    return count;
}
```
