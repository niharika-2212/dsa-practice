# Problem: First unique character in a string

- Platform: Leetcode 387
- Link: https://leetcode.com/problems/first-unique-character-in-a-string/description
- Difficulty: Easy
- Tags: String, counting

## Problem Statement

Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1

## Example

```
Input: s = "leetcode"

Output: 0

Explanation:

The character 'l' at index 0 is the first character that does not occur at any other index.
```

## Approach

- make array to store count of each character
- traverse in the input string and count occurence of each character
- now for each char in string check if the count is 1, if yes return its index

### Time complexity

- Time: `O(s)`
- Space: `O(1)`

### Code (C++)

```c++
int firstUniqChar(string s) {
    vector<int> count(26);
    for(int i=0 ; i<s.size() ; i++){
        count[int(s[i])-97]++;
    }
    int final=-1;
    for(int i=0 ; i<s.size() ; i++){
        if(count[int(s[i])-97]==1){
            final=i;
            break;
        }
    }
    return final;
}
```
