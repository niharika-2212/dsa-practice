# Problem: Binary tree Preorder traversal

- Platform: Leetcode 144
- Link: https://leetcode.com/problems/binary-tree-preorder-traversal/description
- Difficulty: Easy
- Tags: stack, tree, BFS, binary tree

## Problem Statement
Given the root of a binary tree, return the preorder traversal of its nodes' values.

## Example

```
Input: root = [1,null,2,3]

Output: [1,2,3]
```

## Approach 
- create a stack empty
- push root in empty stack
- create vector that will store preorder traversal
- while stack is not empty
    - pop the top value and store it
    - push this value in preorder traversal
    - if top node right is not empty (push it first)
    - if top node left is not empty (push it second)
    - this way when we access top we get left value first for preorder traversal
- return preorder traversal


### Time complexity
- Time: `O(n)` 
- Space: `O(n)`

### Code (C++)
```c++
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> res;
    if(root==NULL){
        return {};
    }
    stack<TreeNode*> s;
        s.push(root);
        while(!s.empty()){
        TreeNode* curr = s.top();
        s.pop();
        res.push_back(curr->val);
        if(curr->right){
            s.push(curr->right);
        }
        if(curr->left){
            s.push(curr->left);
        }
    }
    return res;
}
```
