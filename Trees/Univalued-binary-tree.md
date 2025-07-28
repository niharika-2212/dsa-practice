# Problem: Univalued Binary Tree

- Platform: Leetcode 965
- Link: https://leetcode.com/problems/univalued-binary-tree/description
- Difficulty: Easy
- Tags: tree, BFS, DFS, binary tree 

## Problem Statement
A binary tree is uni-valued if every node in the tree has the same value.

Given the root of a binary tree, return `true` if the given tree is uni-valued, or `false` otherwise.


## Example

```
Input: root = [1,1,1,1,1,null,1]
Output: true
```

## Approach
- keep a compare variable that stores root value
- start from root
- store the first value
- if other values are not equal to compare -> return false;
- if equal check left subtree
- else check right subtree


### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
class Solution {
public:
    int compare=-1;
    bool isUnivalTree(TreeNode* root) {
        
        
        if(root==NULL){
            return true;
        }
        if(compare==-1){
            compare=root->val;
        }
        if(root->val!=compare){
            return false;
        }else{
            bool l = isUnivalTree(root->left);
            if(l==false){
                return false;
            }
            return isUnivalTree(root->right);
        }
    }
};
```
