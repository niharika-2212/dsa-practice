# Problem: Valid Palindrome

- Platform: Neetcode 
- Link: https://neetcode.io/problems/is-palindrome?list=neetcode150
- Difficulty: Easy
- Tags: Two pointers

## Problem Statement
Given a string s, return true if it is a palindrome, otherwise return false.

A palindrome is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

Note: Alphanumeric characters consist of letters (A-Z, a-z) and numbers (0-9).


## Example

```
Input: s = "Was it a car or a cat I saw?"

Output: true
```

## Approach 1
- reverse the string and save in a temporary array
- make sure to remove all non-alphanumeric characters from both
- compare both strings
- if equal return `true`
- else `false`

### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

## Approach 2
- place two pointers (at start and end)
- for each index check if value is alphanumeric
- if not move ahead
- if yes, compare each value, if not equal return `false`
- if equal, check ahead
- when loop completes that means all values were equal, return `true`

### Time complexity
- Time: `O(n)`
- Space: `O(1)`

### Code (C++)
```c++
bool isPalindrome(string s) {
    int i=0 ;
    int j=s.size()-1;
    transform(s.begin(), s.end(), s.begin(), ::tolower);
    while (i <= j)
    {
        // check if both are alphanumeric
        if ((int(s[i]) < 97 &&  int(s[i]) > 57 ) || int(s[i]) > 122 || int(s[i]) < 48 )
        {
            i++;
        }
        else if ((int(s[j]) < 97 &&  int(s[j]) > 57 ) || int(s[j]) > 122 || int(s[j]) < 48)
        {
            j--;
        }
        else
        {
            if (s[i] == s[j])
            {
                i++;
                j--;
            }
            else
            {
                return false;
            }
        }
    }
    return true;
}
```
