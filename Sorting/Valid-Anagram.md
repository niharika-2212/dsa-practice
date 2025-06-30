# Problem: Valid Anagram

- Platform: Leetcode 242
- Link: https://leetcode.com/problems/valid-anagram/description
- Difficulty: Easy
- Tags: Hash Table, String, Sorting

## Problem Statement

Given two strings s and t, return `true` if t is an anagram of s, and `false` otherwise.

## Example

```
Input: s = "anagram", t = "nagaram"
Output: true
```

## Approach 1
- count occurences of all alphabets in two arrays : `count_s` and `count_t`
- compare `count_s` array and `count_t` array: if equal return `true` else `false`

### Time complexity
- Time: `O(n+m)` 
- Space: `O(1)`

### Code (C++)
```c++
bool isAnagram(string s, string t) {
        vector<int> count_s(26), count_t(26);
        for(int i=0 ; i<s.length() ; i++){
            count_s[int(s[i])-97]++;
        } 
        for(int i=0 ; i<t.length() ; i++){
            count_t[int(t[i])-97]++;
        } 
        for(int i=0 ; i<26 ; i++){
            if(count_s[i]!=count_t[i]){
                return false;
            }
        }
        return true;
    }
```


## Approach 2 (NOT GOOD)
- sort both arrays
- now if both arrays are equal(same elements) return `true` else `false`

### Time complexity
- Time: `O(nlogn+mlogm)` 
- Space: `O(1)`
