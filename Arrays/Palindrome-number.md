# Problem: Palindrome number
- Platform: Leetcode 9
- Link: https://leetcode.com/problems/palindrome-number/description
- Difficulty: Easy
- Tags: Math

## Problem Statement
Given an integer x, return true if x is a palindrome, and false otherwise.
Can you solve this question without converting to string

## Example
```
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
```
```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

## Approach 
- if input is negative it can never be palindrome return `false`
- copy input to another variable
- store reverse integer in another variable `rev`
- insert in `rev = rev*10+digit` and remove digit from input number till empty 
- if `rev = input` number(saved in another variable) return tr`ue else `false`

### Time complexity
- Time: `O(n)`
- Space: `O(1)` 



### Code (C++)
```c++
bool isPalindrome(int x){
        if(x<0){
            return false;
        }
        long long rev=0, old=x;
        while(old>0){
            int temp=old%10;
            rev=rev*10+temp;
            old=old/10;
        }
        if(rev==x){
            return true;
        }
        else{
            return false;
        }
    }
```