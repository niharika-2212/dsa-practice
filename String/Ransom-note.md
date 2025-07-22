# Problem: Ransom note

- Platform: Leetcode 383
- Link: https://leetcode.com/problems/ransom-note/description/
- Difficulty: Easy
- Tags: Hash table, string, counting 

## Problem Statement
Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.


## Example
```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

## Approach 
- create two vector for alphabet count in each string
- if ransomnote is greater than magazine (return false)
- if less
    - count alphabets in each string
    - now compare the two vectors
    - if value ransom is <= mag (move forward)
    - if ransome is greater value return false


### Time complexity
- Time: `O(n+m)` 
- Space: `O(1)`

### Code (C++)
```c++
bool canConstruct(string ransomNote, string magazine) {
    vector<int>ransom(26);
    vector<int>mag(26);
    if(ransomNote.size()>magazine.size()){
        return false;
    }else{
        for(int i=0 ; i<ransomNote.size() ; i++){
            int temp = int(ransomNote[i])-97;
            ransom[temp]++;
        }
        for(int i=0 ; i<magazine.size() ; i++){
            int temp = int(magazine[i])-97;
            mag[temp]++;
        }
        for(int i=0 ; i<mag.size() ; i++){
            if(mag[i]>=ransom[i]){
                continue;
            }else{
                return false;
            }
        }
        return true;
    }
}
```
