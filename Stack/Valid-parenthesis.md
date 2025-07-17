# Problem: Valid Parentheses

- Platform: Leetcode 20
- Link: https://leetcode.com/problems/valid-parentheses/description
- Difficulty: Easy
- Tags: string, stack

## Problem Statement
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.


## Example

```
Input: s = "()[]{}"
Output: true
```

## Approach 
- create a stack
- for each opening brace push in stack
- for each closing brace, if top of the stack has same brace open pop the element
- if not same, return false (not valid)
- at the end, if everything went well the stack is empty then return true

### Time complexity
- Time: `` 
- Space: ``

### Code (C++)
```c++
class Solution {
public:
    bool isEmpty(int top){
        if(top<0){
            return true;
        }
        else{
            return false;
        }
    }
    bool isValid(string s) {
        int top=-1;
        int capacity=s.size();
        vector<char> arr (capacity);
        for(int i=0 ; i<s.size() ; i++){
            if(s[i]=='(' || s[i]=='{' || s[i]=='['){
                top++;
                arr[top]=s[i];
            }
            else {
                if(!isEmpty(top) && s[i]==')' && arr[top]=='('){
                    top--;
                }
                else if(!isEmpty(top) && s[i]=='}' && arr[top]=='{'){
                    top--;
                }
                else if(!isEmpty(top) && s[i]==']' && arr[top]=='['){
                    top--;
                }
                else {
                    return false;
                }
            }
        }
        if(isEmpty(top)){
            return true;
        }else{
            return false;
        }
    }
};
```
