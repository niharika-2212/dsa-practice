# Problem: Clear Digits

- Platform: Leetcode 3174
- Link: https://leetcode.com/problems/clear-digits/description
- Difficulty: Easy
- Tags: string, stack

## Problem Statement
You are given a string s.

Your task is to remove all digits by doing this operation repeatedly:

Delete the first digit and the closest non-digit character to its left.
Return the resulting string after removing all digits.

Note that the operation cannot be performed on a digit that does not have any non-digit character to its left.


## Example

```
Input: s = "cb34"

Output: ""

Explanation:

First, we apply the operation on s[2], and s becomes "c4".

Then we apply the operation on s[1], and s becomes "".
```

## Approach 
- create a stack
- traverse in string
- if non-digit, push the element
- if digit, check for top element in stack
    - if non-digit pop the element
    - if digit, push the current element
- convert the remaining stack at the end of traversal to string
- return string


### Time complexity
- Time: `O(s)` 
- Space: `O(s)`

### Code (C++)
```c++
string clearDigits(string s) {
    vector<char>final(0);
    for(int i=0 ; i<s.size() ; i++){
        if(int(s[i])>=48 && int(s[i])<=57){
            if(int(final[final.size()-1])<48 || int(final[final.size()-1])>57){
                final.pop_back();
            }else{
                final.push_back(s[i]);
            }
        }else{
            final.push_back(s[i]);
        }
    }
    string s_new="";
    for(int i=0 ; i<final.size() ; i++){
        s_new+=final[i];
    }
    return s_new;
}
```
