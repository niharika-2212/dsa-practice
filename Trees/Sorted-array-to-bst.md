# Problem: Convert Sorted Array to Binary Search Tree

- Platform: Leetcode 108
- Link: https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description
- Difficulty: Easy
- Tags: Array, Divide and Conquer. Tree, BST, Binary Tree

## Problem Statement
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

## Example

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
```

## Approach
- since it is sorted array, it also is inorder traversal of the tree
- start from the mid of this array-> this will be root
- root->left will be from left to mid
- root->right will be from mid to right
- return the root of your balanced bst

### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
TreeNode* buildTree(vector<int>& nums, int l, int r){
    if(l>r){
        return NULL;
    }
    int mid = l + (r-l)/2;
    TreeNode* root = new TreeNode(nums[mid]);
    root->left = buildTree(nums, l, mid-1);
    root->right = buildTree(nums, mid+1, r);
    return root;
}

TreeNode* sortedArrayToBST(vector<int>& nums) {
    int l=0;
    int r = nums.size()-1;
    TreeNode* node = buildTree(nums,l,r);
    return node;
}
```
