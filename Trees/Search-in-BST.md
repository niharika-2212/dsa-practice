# Problem: Search in a Binary Search Tree

- Platform: Leetcode 700
- Link: https://leetcode.com/problems/search-in-a-binary-search-tree/description
- Difficulty: Easy
- Tags: tree, BST, binary tree

## Problem Statement
You are given the root of a binary search tree (BST) and an integer val.

Find the node in the BST that the node's value equals val and return the subtree rooted with that node. If such a node does not exist, return null.

## Example

```
Input: root = [4,2,7,1,3], val = 2
Output: [2,1,3]
```

## Approach 
- if node null return null (not found)
- if value < node
    - search in left subtree
- if value > node
    - search in right subtree
- if value==null
    - return node


### Time complexity
- Time: `O(h)` 
- Space: `O(h)`

### Code (C++)
```c++
TreeNode* searchBST(TreeNode* root, int val) {
        if(root==NULL){
            return NULL;
        }
        if(val < root->val){
            return searchBST(root->left, val);
        } else if(val > root->val ){
            return searchBST(root->right, val);
        }else{
            return root;
        }
    }
```
