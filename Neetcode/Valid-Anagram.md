# Problem: Valid anagram

- Platform: Neetcode
- Link: https://neetcode.io/problems/is-anagram?list=neetcode150
- Difficulty: Easy
- Tags: Array and hashing

## Problem Statement
Given two strings s and t, return true if the two strings are anagrams of each other, otherwise return false.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.


## Example

```
Input: s = "racecar", t = "carrace"

Output: true
```

## Approach 1
- Sort the array
- if both arrays are equal return `true`
- else return `false`

### Time complexity
- Time: `O(slogs + tlogt)` 
- Space: `O(1)`

## Approach 2
- count frequency of each letter in s
- subtract each letter frequency in t
- if both are anagram, letter frequencies must be same 
- hence final frequencies of all letter must be 0
- if not 0 return `false`
- else return `true`

### Time complexity
- Time: `O(s + t)` 
- Space: `O(1)`

### Code(c++)
```c++
bool isAnagram(string s, string t) {
    vector<int> temp (26);
    // vector<int> t1 (26);/
    if(s.size()!=t.size()){
        return false;
    }else{
        for(int i=0 ; i<s.size() ; i++){
            temp[int(s[i]-97)]++;
        }
        for(int i=0 ; i<t.size() ; i++){
            temp[int(t[i]-97)]--;
        }
    }
    for(int i=0 ; i<temp.size() ; i++){
        if(temp[i]!=0){
            return false;
        }
    }
    return true;
}
```
