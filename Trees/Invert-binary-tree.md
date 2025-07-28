# Problem: Invert binary tree

- Platform: Leetcode 226
- Link: https://leetcode.com/problems/invert-binary-tree/description
- Difficulty: Easy
- Tags: tree, DFS, BFS, binary tree

## Problem Statement
Given the root of a binary tree, invert the tree, and return its root.


## Example

```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```
![alt text](image.png)

## Approach 1
- start from root
- swap left and right tree
- repeat same for left subtree
- repeat same for right subtree


### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
TreeNode* invertTree(TreeNode* root) {
    if(root==NULL){
        return root;
    }
    // swap left and right tree
    TreeNode* temp = root->left;
    root->left=root->right;
    root->right = temp;
    // repeat for left tree
    TreeNode* left = invertTree(root->left);
    // repeat for right tree
    TreeNode* right = invertTree(root->right);
    return root;
}
```
