# Problem: Add Binary

- Platform: Leetcode 67
- Link: https://leetcode.com/problems/add-binary/description/
- Difficulty: Easy
- Tags: math, string, bit manipulation, math

## Problem Statement
Given two binary strings a and b, return their sum as a binary string.


## Example

```
Input: a = "11", b = "1"
Output: "100"
```

## Approach
- naive approach
- if both strings are not equal in size make them equal by adding 0s to smaller string
- now start from end
- add the two binary digits and store in string
- return string

| A | B | Carry | result | carry |
| - | - | - | - | - |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

### Time complexity
- Time: `O(a)` 
- Space: `O(1)`

### Code (C++)
```c++
string addBinary(string a, string b) {
    if (a.size() > b.size()) {
        while (a.size() != b.size()) {
            b = '0' + b;
        }
    }
    if (a.size() < b.size()) {
        while (a.size() != b.size()) {
            a = '0' + a;
        }
    }
    char carry = '0';
    string final = "";
    for (int i = b.size() - 1; i >= 0; i--) {
        if (a[i] == '0' && b[i] == '0') {
            if (carry == '0') {
                final = '0' + final;
                carry='0';
            }
            else if(carry=='1'){
                final='1'+final;
                carry='0';
            }
        }else if((a[i]=='0' && b[i]=='1') || (a[i]=='1' && b[i]=='0')){
            if(carry=='0'){
                final='1'+final;
                carry='0';
            }
            else if(carry=='1'){
                final = '0' + final;
                carry='1';
            }
        }else if(a[i]=='1' && b[i]=='1'){
            if(carry=='0'){
                final='0'+final;
                carry='1';
            }
            else if(carry=='1'){
                final='1'+final;
                carry='1';
            }
        }
    }
    if(carry=='1'){
        final=carry+final;
    }
    return final;
}
```
