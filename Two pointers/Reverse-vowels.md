# Problem: Reverse vowels of a string

- Platform: Leetcode 345
- Link: https://leetcode.com/problems/reverse-vowels-of-a-string/description
- Difficulty: Easy
- Tags: Two pointers, string

## Problem Statement
Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.


## Example

```
Input: s = "IceCreAm"

Output: "AceCreIm"

Explanation:

The vowels in s are ['I', 'e', 'e', 'A']. On reversing the vowels, s becomes "AceCreIm".
```

## Approach 
- maintain two pointer
- at start and end
- traverse from both ends
- if both have vowels swap
- else move forward

### Time complexity
- Time: `O(s)` 
- Space: `O(1)`

### Code (C++)
```c++
string reverseVowels(string s) {
        int i=0 ; 
        int j=s.size()-1;
        while(i<=j){
            if(isvowel(s[i]) && isvowel(s[j])){
                // swap;
                char t = s[i];
                s[i]=s[j];
                s[j]=t;
                i++;
                j--;
            }else if(isvowel(s[i]) && !isvowel(s[j])){
                j--;
            }else if(!isvowel(s[i]) && isvowel(s[j])){
                i++;
            }else{
                i++;
                j--;
            }
            
        }
        return s;
    }
    public:
        bool isvowel(char c){
            if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u' || c=='A' || c=='E' || c=='I' || c=='O' || c=='U'){
                return true;
            }else{
                return false;
            }
        }
```
