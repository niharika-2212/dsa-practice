# Problem: Same tree

- Platform: Leetcode 100
- Link: https://leetcode.com/problems/same-tree/description
- Difficulty: Easy
- Tags: tree, BFS, DFS, binary tree

## Problem Statement
Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.


## Example

```
Input: p = [1,2,3], q = [1,2,3]
Output: true
```

## Approach
- using DFS
- check from bottom
- if both values null
    - return `true`
- if either null
    - return `false`
- if neither null
    - if values are not equal return `false`
    - check if their values are equal
    - if equal move to children left
    - check if left tree gives `false` return `false` (no need to check right tree will not be same)
    - if left tree is same check right
    - if right tree is also same return `true`


### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
bool isSameTree(TreeNode* p, TreeNode* q) {
    if(p==NULL && q==NULL){
        return true;
    }
    if(p==NULL && q!=NULL){
        return false;
    }
    if(p!=NULL && q==NULL){
        return false;
    }
    if(p->val!=q->val){
        return false;
    }
    bool left = isSameTree(p->left, q->left);
    if(left==false){
        return false;
    }
    return isSameTree(p->right, q->right);
        
}
```
